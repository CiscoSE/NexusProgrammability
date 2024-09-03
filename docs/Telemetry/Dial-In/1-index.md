# Dial-In Overview

## About Dial-In Telemetry
Dial-in telemetry uses model-driven methods to collect telemetry from a Cisco Nexus device. The term "dial-in" means the external collector is "dialing-in" to the Nexus device and telling the switch what to send. This process happens in two steps. The first step is for the external collector to connect to the Nexus device and tell the switch which telemetry data to collect. The second step is for the Nexus device to send this data to the external collector.

Dial-in telemetry has multiple methods available for the data structure, encoding, and transport.

## Dial-In Telemetry Features
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

## About gRPC
Google Remote Procedure Call (gRPC) is an open source high performance RPC framework released in 2016. gRPC has many RPCs available to control systems. It uses HTTP/2 for transport, protocol buffers for the interface description language, and includes the following features:

* Authentication
* Bi-directional streaming
* Bi-direction flow control
* Blocking bindings
* Non-blocking bindings
* Cancellation
* Timeouts

gRPC can generate cross-platform client and server bindings for many languages. It also supports TLS and token-based authentication. gRPC uses protocol buffers to encode data.

## About gNMI
gRPC Network Management Interface (gNMI) is a specific set of RPCs built on top of gRPC. It can be used for programming a remote device, or collecting information from a remote device. The content provided through gNMI can be modeled using YANG. gRPC carries gNMI and provides the ability to create and transmit requests.

## NX-OS gNMI Features
NX-OS supports the following gNMI RPCs:

* Get - Collect telemetry data from a device one time.
* Set - Modify the configuration of a device.
* Subscribe - Subscribe to an indefinite stream of telemetry data from a device.
* Capabilities - Collect the gNMI capabilities supported on a device.

## gNMI Subscription
The most commonly used gNMI RPC is the subscribe RPC. Starting in NX-OS 9.3.1, Nexus switches support the following gNMI subscription features:

* Once
    * Collect current values only once.
* Poll
    * When the switch receives a poll message, it will send current values.
* Stream - Sample
    * Collect current values every stream interval. Supported time interval ranges are from 1 to 604800 seconds. The default sample time is 10 seconds.
* Stream - On_Change
    * Collect current values immediately. After this initial collection, only collect values when there is a change.
* Stream - Target_Defined
    * This allows the switch to select the best type of subscription to use (either sample or on_change).