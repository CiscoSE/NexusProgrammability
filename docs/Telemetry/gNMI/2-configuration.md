# gNMI Device Configuration
gNMI relies on gRPC. A combination of gRPC and gNMI settings are required to configure this functionality on NX-OS.

#### Enable gRPC
Enable the gRPC agent.
```
switch# feature grpc
```

#### Configure gRPC Port
Configure the port number used for gRPC.
```
switch# grpc port 50051
```
!!! Note
    Ports can be from 1024 to 65535. Default is 50051.

#### Configure Certificate
Specify the certificate trustpoint ID used for gRPC.
```
switch# grpc certificate TRUSTPOINT
```
!!! Note
    TRUSTPOINT is the name of your trustpoint ID. For more information, see [Installing Identity Certificates](https://www.cisco.com/c/en/us/td/docs/dcn/nx-os/nexus9000/103x/configuration/security/cisco-nexus-9000-nx-os-security-configuration-guide-103x/m-configuring-pki.html#task_2088148)

#### Set Dial-In Call Limits
Set the limit of simultaneous dial-in calls to the gNMI server on the device.
```
switch# grpc gnmi max-concurrent-call 8
```
!!! Note
    - The limit can be from 1 to 16. Default is 8.
    - This value applies to each VRF configured. If your limit is set to 4 and you have 2 VRFs configured, the total limit is 8.

#### Configure VRF
Allow the gRPC agent to accept requests on specified VRFs.
```
switch# grpc use-vrf default
```
!!! Note
    By default, the management VRF accepts incoming requests when the gRPC feature is enabled.