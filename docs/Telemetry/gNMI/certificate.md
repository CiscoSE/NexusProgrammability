# Certificate requirements for secure connections

NX-OS supports two types of certificates for gRPC:

- Server certificate: Used to encrypt the gRPC connection between the client and the device (in this case, the gNMI server or target)
- Client certificate: Used to authenticate a gRPC connection

> To create any type of certificate, a certificate authority (CA) is required. If you don't have one (or you are looking for something free), follow the steps in this excelent guide by Jamie Nguyen: https://jamielinux.com/docs/openssl-certificate-authority/introduction.html

> An acurate time is important when dealing with TLS certificates. It is recommended to setup NTP in the client and servers/devices. If you see errors related to certificate not valid yet or expired it is probably that the device or the client don't have a correct time set.

> For simplicity, this tutorial uses root but other users with less priviledges can be used. 

> Make sure keys and certificates are protected

> Tests for this tutorial are done using [gnmic](https://github.com/karimra/gnmic) and [pygnmi](https://pypi.org/project/pygnmi/)

## Server certificate

A server certificate will allow you to connect to a NX-OS device securely, without need of skipping TLS verification for TLS connections. 

> It is assumed that you have a valid root and intermediate CA certificates. Instructions can be found at the top of this article on how to set that up 
> 

#### Add the subjectAltName setting to the intermediate/openssl.cnf file (server_cert section):

```
[ server_cert ]
# Extensions for server certificates (`man x509v3_config`).
basicConstraints = CA:FALSE
subjectAltName=${ENV::SAN}
nsCertType = server
nsComment = "OpenSSL Generated Server Certificate"
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid,issuer:always
keyUsage = critical, digitalSignature, keyEncipherment
extendedKeyUsage = serverAuth
```

The value _${ENV::SAN}_ instructs openssl to look for the value of the subjectAltName in an environmental variable called _SAN_

#### Set the SAN variable. If you don't have a DNS available, you can manually add the host entry in the /etc/hosts file if you would like to use names instead of IPs. Either one works

In this example, the device name is nx93000v-01.cisco.com and its management IP is 192.168.1.1

```bash
export SAN=DNS:nx9300v-01,DNS:nx9300v-01.cisco.com,IP:192.168.1.1
```
#### Create keys and certificates. Altough the file name is trivial, it is a best practice to use the hostname of the device or other identifier that sumarizes the purpuse of the certificate. 

> You can use the same certificate for multiple devices
> Make sure to use server_cert extensions

```bash
openssl genrsa -out intermediate/private/nx9300v-01.cisco.com.key.pem

openssl req -config intermediate/openssl.cnf -key intermediate/private/nx9300v-01.cisco.com.key.pem -new -sha256 -out intermediate/csr/nx9300v-01.cisco.com.csr.pem
(...)
-----
Country Name (2 letter code) [GB]:US
State or Province Name [England]:CO
Locality Name []:
Organization Name [Alice Ltd]:Nexus
Organizational Unit Name []:Datacenter 
Common Name []:nx9300v-01.cisco.com
Email Address []:

openssl ca -config intermediate/openssl.cnf -extensions server_cert -days 375 -notext -md sha256 -in intermediate/csr/nx9300v-01.cisco.com.csr.pem -out intermediate/certs/nx9300v-01.cisco.com.cert.pem
```
#### Verify the certificate has been generated correctly. Check that alternative name section is present and has the values set in the previous step

```bash
openssl x509 -noout -text -in intermediate/certs/nx9300v-01.cisco.com.cert.pem
```
#### To import the certificate and key into the device, we need to chain the ca, intermediate and device certificate into a single file

```bash
cat intermediate/certs/nx9300v-01.cisco.com.cert.pem > intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
cat intermediate/certs/intermediate.cert.pem >> intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
cat certs/ca.cert.pem >> intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
```
#### Using pkcs12, export and copy the file to the device. Make sure to remember the password

```bash
openssl pkcs12 -export -out intermediate/certs/nx9300v-01.cisco.com.pfk -inkey intermediate/private/nx9300v-01.cisco.com.key.pem -in intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
scp intermediate/certs/nx9300v-01.cisco.com.pfk  admin@192.168.1.1:
```
#### Import the pkcs12 file (For this example, "supersecret" was used as password the step before) and configure grpc to use that truspoint

```cli
configure
crypto ca trustpoint server
crypto ca import server pkcs12 bootflash:nx9300v-01.cisco.com.pfk supersecret
grpc certificate server
```
#### Test with gnmic - make sure to use the certificate chains files, not the standalone certificate file. The --skip-verify option should not be needed

```
# gnmic -a nx9300v-01.cisco.com:50051 -u admin -p YOURPASSWORD get --path /System/name --tls-cert intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem --tls-key intermediate/private/nx9300v-01.cisco.com.key.pem -e json --tls-ca intermediate/certs/ca-chain.cert.pem 
[
    {
    "source": "nx9300v-01.cisco.com:50051",
    "timestamp": 1657660857691587822,
    "time": "2022-07-12T21:20:57.691587822Z",
    "updates": [
        {
        "Path": "System/name",
        "values": {
            "System/name": "nx9300v-01"
        }
        }
    ]
    }
]
# 
```
#### Other libraries like pygnmi should work too. For example:

> For simplicity, this example includes credentials in clear text, which is not a best practice.

```python
# Modules
from pygnmi.client import gNMIclient
import json
# Variables
host = ('nx9300v-01.cisco.com', '50051')
paths = ['/System/name']

# Body
if __name__ == '__main__':
    with gNMIclient(target=host, username='admin', password="YOURPASSWORD", path_cert="./ca/intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem",
    path_key="./ca/intermediate/private/nx9300v-01.cisco.com.key.pem", path_root="./ca/intermediate/certs/ca-chain.cert.pem") as gc:

            result = gc.get(path=paths, encoding='json')
            print(result)
            print()
```


```
# 
# python get-nx.py 
{'notification': [{'timestamp': 1657660901108756130, 'update': [{'path': 'System/name', 'val': 'nx9300v-01'}]}]}

# 
```

## Client certificate

If you prefer to use a certificate instead of a password, you can create a client certificate that can be used to authenticate against the NX-OS device.

> It is assumed that you have a valid root and intermediate CA certificates. Instructions can be found at the top of this article on how to set that up 

1. Create keys and certificates. Altough the file name is trivial, it is a best practice to use the username or other identifier that sumarizes the purpuse of the certificate, csr and keys. 

> You can use the same certificate to login to multiple devices with the same username
> Make sure to use usr_cert extensions
> Use the username as value for _Common Name_ and _Organizational Unit Name_

```
# openssl genrsa -out intermediate/private/admin.key.pem 2048

# openssl req -config intermediate/openssl.cnf -key intermediate/private/admin.key.pem -new -sha256 -out intermediate/csr/admin.csr.pem
-----
Country Name (2 letter code) [GB]:US
State or Province Name [England]:CO
Locality Name []:
Organization Name [Alice Ltd]:Nexus
Organizational Unit Name []:admin
Common Name []:admin
Email Address []:

# openssl ca -config intermediate/openssl.cnf -extensions usr_cert -days 375 -notext -md sha256 -in intermediate/csr/admin.csr.pem -out intermediate/certs/admin.cert.pem
```

2. Create a certificate chain

```bash
cat intermediate/certs/admin.cert.pem > intermediate/certs/admin.chain.cert.pem 
cat intermediate/certs/intermediate.cert.pem >> intermediate/certs/admin.chain.cert.pem
cat certs/ca.cert.pem >> intermediate/certs/admin.chain.cert.pem
```

3. Import the CA certificate into the device with a new trustpoint. For this example, gnmi-root is used but it can have any name. Use the content of the root certificate only in certs/ca.cert.pem, no chains or intermediate cert are required

```
nx9300v_01# configure
nx9300v_01(config)# crypto ca trustpoint gnmi-root
nx9300v_01(config)# crypto ca authenticate gnmi-root
input (cut & paste) CA certificate (chain) in PEM format;
end the input with a line containing only END OF INPUT :
-----BEGIN CERTIFICATE-----
(...)
-----END CERTIFICATE-----
END OF INPUT
(...)

Do you accept this certificate? [yes/no]:yes

nx9300v_01(config)# grpc client root certificate gnmi-root
```

4. Create a .gnmic.yaml configuration file with the following content:

> You might need to change the tls files path to match your environment
> Password is not required anymore

```
# cat .gnmic.yaml
log-file: /tmp/gnmic.log
debug: true
tls-ca: ./intermediate/certs/ca-chain.cert.pem
targets:
  192.168.1.2:50051:
    username: admin
    tls-cert: ./intermediate/certs/admin.chain.cert.pem
    tls-key: ./intermediate/private/admin.key.pem 
```

5. Test with gnmic 

```
# gnmic get --path /System/name 
[
  {
    "source": "192.168.1.2:50051",
    "timestamp": 1663693091279809206,
    "time": "2022-09-20T12:58:11.279809206-04:00",
    "updates": [
      {
        "Path": "System/name",
        "values": {
          "System/name": "nx9300v_01"
        }
      }
    ]
  }
]
# 
```


