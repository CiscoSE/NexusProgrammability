# Dial-Out Overview

## About Dial-Out Telemetry
Dial-out telemetry uses model-driven methods to receive telemetry from a Cisco Nexus device. The term "dial-out" means the Nexus device is "dialing-out" to us and sending us telemetry data. This process happens without any action from an external source.

Dial-out telemetry has multiple methods available for the data structure, encoding, and transport.

## Dial-Out Telemetry Features
Supports the following data structure types:

* DME
* Cisco Native YANG
* OpenConfig YANG

Supports the following encoding types:

* JSON
* GPB Compact
* GPB Key-Value

Supports the following transport types:

* HTTP
* gRPC

## Limitations
* The dial-out telemetry service on NX-OS is limited to 20% of the CPU resource.
* The telemetry service cannot send more than 12 MB of data in one push. If you are collecting large amounts of data, it is possible to exceed the 12 MB limit. If this occurs, the telemetry service will drop the remaining payload in order to maintain a size of 12 MB.
In order to ensure large amounts of data can be sent, you must enable gRPC chunking in your telemetry configuration. gRPC chunking allows the Nexus device to fragment the telemetry data, and requires the collector to reassemble the data. NX-OS accepts chunking sizes from 64 to 4096 bytes.