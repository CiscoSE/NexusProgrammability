# Certificate requirements for secure connections

As per [gnmi specification](https://github.com/openconfig/reference/blob/master/rpc/gnmi/gnmi-specification.md#31-session-security-authentication-and-rpc-authorization):
!!! quote "3.1 Session Security, Authentication and RPC Authorization"
    The session between the client and server MUST be encrypted using TLS - and a target or client MUST NOT fall back to unencrypted sessions.

NX-OS only supports TLS connection on gRPC, mTLS is supported since NX-OS 10.1(1). There are two certificates required in this process:

- Server certificate: Used to encrypt the gRPC connection between the client and the device (in this case, the gNMI server or target)
- Client certificate: Used to authenticate a gRPC connection

To create any type of certificate, a certificate authority (CA) is required. If you don't have one (or you are looking for something that is free), follow the steps in this guide by Jamie Nguyen: [OpenSSL Certificate Authority](https://jamielinux.com/docs/openssl-certificate-authority/introduction.html)

Accurate time is important when dealing with TLS certificates. It is recommended to setup NTP on the client and servers/devices. If you see errors related to the certificate not being valid yet or expired, it is probably due to the client or server having the incorrect time set.

For simplicity, this tutorial uses root but other users with less privileges can be used.

Make sure your keys and certificates are protected.

Tests for this tutorial are done using [gNMIc](https://github.com/openconfig/gnmic) and [pygNMI](https://pypi.org/project/pygnmi/)

## Server certificate

A server certificate will allow you to connect to an NX-OS device securely, without the need to skip TLS verification for TLS connections.

!!! note
    It is assumed that you have a valid root and intermediate CA certificates installed in your workstation. Instructions can be found at the top of this article on how to set that up.

#### Add the subjectAltName option

gRPC does not use the CN attribute of the certificate to verify hostname. Add the `subjectAltName=${ENV::SAN}` option to the /root/ca/intermediate/openssl.cnf file. This will be added in the [ server_cert ] section.

server_cert example:

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

The value `${ENV::SAN}` instructs openssl to look for the value of the subjectAltName in an environmental variable called _SAN_

#### Set the SAN variable. 

If you don't have a DNS available, you can manually add the host entry in the /etc/hosts file if you would like to use names instead of IPs. Either one works.

In this example, the device name is nx93000v-01.cisco.com and its management IP is 192.168.1.1.

```bash
export SAN=DNS:nx9300v-01,DNS:nx9300v-01.cisco.com,IP:192.168.1.1
```

#### Create key and certificate 

Although the file name is trivial, it is a best practice to use the hostname of the device or other identifier that summarizes the purpose of the certificate.

!!! note
    The following commands are intended to be run from `/root/ca`
    You can use the same certificate for multiple devices. Make sure to use server_cert extensions.

```bash
openssl genrsa -out intermediate/private/nx9300v-01.cisco.com.key.pem
```
```
openssl req -config intermediate/openssl.cnf -key intermediate/private/nx9300v-01.cisco.com.key.pem -new -sha256 -out intermediate/csr/nx9300v-01.cisco.com.csr.pem
```

??? example "Output"
    ```
    (...)
    -----
    Country Name (2 letter code) [GB]:US
    State or Province Name [England]:CO
    Locality Name []:
    Organization Name [Alice Ltd]:Nexus
    Organizational Unit Name []:Datacenter
    Common Name []:nx9300v-01.cisco.com
    Email Address []:
    ```

```
openssl ca -config intermediate/openssl.cnf -extensions server_cert -days 375 -notext -md sha256 -in intermediate/csr/nx9300v-01.cisco.com.csr.pem -out intermediate/certs/nx9300v-01.cisco.com.cert.pem
```
#### Verify the certificate 

Check that the alternative name section is present and has the values set in the previous step

```bash
openssl x509 -noout -text -in intermediate/certs/nx9300v-01.cisco.com.cert.pem
```
??? example "Output"
    ```
    X509v3 Subject Alternative Name:
    DNS:nx9300v-01, IP Address:192.168.1.1
    ```

#### Create the certificate chain

```bash
cat intermediate/certs/nx9300v-01.cisco.com.cert.pem > intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
cat intermediate/certs/intermediate.cert.pem >> intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
cat certs/ca.cert.pem >> intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
```
#### Export the file into the device. 

!!! note
    Make sure to export the password. Also, your NX-OS device will need the `scp-server` feature enabled to accept the SCP transfer.

```bash
openssl pkcs12 -export -out intermediate/certs/nx9300v-01.cisco.com.pfk -inkey intermediate/private/nx9300v-01.cisco.com.key.pem -in intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem
scp intermediate/certs/nx9300v-01.cisco.com.pfk  admin@192.168.1.1:
```
#### Import the pkcs12 file 

Execute the following commands on the device. For this example, "supersecret" was used as the password. 

```cli
nx9300v_01# configure
nx9300v_01(config)# crypto ca trustpoint server
nx9300v_01(config)# crypto ca import server pkcs12 bootflash:nx9300v-01.cisco.com.pfk supersecret
```

Configure grpc to use the truspoint above:
```
nx9300v_01(config)# grpc certificate server
```
#### Test with gnmic

Use the certificate chain file, not the standalone certificate file. The `--skip-verify` option should not be needed

```
gnmic -a nx9300v-01.cisco.com:50051 -u admin -p YOURPASSWORD get --path /System/name --tls-cert intermediate/certs/nx9300v-01.cisco.com.chain.cert.pem --tls-key intermediate/private/nx9300v-01.cisco.com.key.pem -e json --tls-ca intermediate/certs/ca-chain.cert.pem
```

??? example "Output"

    ```json
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
    ```

#### Test with pygnmi

!!! note 
    For simplicity, this example includes credentials in clear text, which is not a best practice.

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
```


```
# python get-nx.py 
```
??? example "Output"
    ```json
    {'notification': [{'timestamp': 1657660901108756130, 'update': [{'path': 'System/name', 'val': 'nx9300v-01'}]}]}

    ```

## Client certificate

If you prefer to use a certificate and key instead of a password, you can create a client certificate that can be used to authenticate against the NX-OS device.
It is assumed that you have a valid root and intermediate CA certificates installed in your workstation. Instructions can be found at the top of this article on how to set that up.

#### Create key and certificate

Although the file name is trivial, it is a best practice to use the username or other identifier that sumarizes the purpose of the certificate, csr and keys.

!!! note 
     - Make sure to use usr_cert extensions
     - Use the username as value for _Common Name_ and _Organizational Unit Name_

Generate private key:
```
openssl genrsa -out intermediate/private/admin.key.pem 2048
```

Create CSR:

```
openssl req -config intermediate/openssl.cnf -key intermediate/private/admin.key.pem -new -sha256 -out intermediate/csr/admin.csr.pem
```

??? example
    ```
    -----
    Country Name (2 letter code) [GB]:US
    State or Province Name [England]:CO
    Locality Name []:
    Organization Name [Alice Ltd]:Nexus
    Organizational Unit Name []:admin
    Common Name []:admin
    Email Address []:
    ```

Sign the certificate: 
```
openssl ca -config intermediate/openssl.cnf -extensions usr_cert -days 375 -notext -md sha256 -in intermediate/csr/admin.csr.pem -out intermediate/certs/admin.cert.pem
```

#### Create the certificate chain

```bash
cat intermediate/certs/admin.cert.pem > intermediate/certs/admin.chain.cert.pem 
cat intermediate/certs/intermediate.cert.pem >> intermediate/certs/admin.chain.cert.pem
cat certs/ca.cert.pem >> intermediate/certs/admin.chain.cert.pem
```

#### Import the CA certificate 

For this example, gnmi-root is used as trustpoint name but it can have any name. Use the content of the **root certificate** only (certs/ca.cert.pem) - no chains or intermediate certs are required, when client authenticates with nxos using certificate, it needs to provide the chain of certificates(root certificate can be ommited).

Execute the following commands on the device:

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
```

Configure the grpc client root certificate:
```
nx9300v_01(config)# grpc client root certificate gnmi-root
```

#### Create gnmic config file

You might need to change the tls files path to match your environment
Password is not required anymore

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

#### Test with gnmic 

```
# gnmic get --path /System/name 
```
??? example "Output"
    ```json
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
    ```
