# gNMI Overview

## About gRPC
gNMI is built on top of Google Remote Procedure Call (gRPC). gRPC is an open source high performance RPC framework released in 2016. It uses HTTP/2 for transport, protocol buffers for the interface description language, and includes the following features:

* authentication
* bi-directional streaming
* bi-direction flow control
* blocking bindings
* non-blocking bindings
* cancellation
* timeouts

gRPC can generate cross-platform client and server bindings for many languages. It also supports TLS and token-based authentication. gRPC uses protocol buffers to encode data.

## About gNMI
gRPC Network Management Interface (gNMI) is a specification of RPCs for managing or collecting the state of a device. The content provided through gNMI can be modeled using YANG. gRPC carries gNMI and provides the ability to create and transmit requests.

## NX-OS gNMI Features
gNMI can be transmitted in two ways:

* Dial-In
    * In this mode, the client will initiate the connection to the switch.
* Dial-Out
    * In this mode, the switch will initiate the connection to the client.

NX-OS supports the following gNMI RPCs:

* Get
* Set
* Subscribe
* Capabilities

## gNMI Subscription
gNMI subscription can be used with both dial-in or dial-out methods.

* For dial-in subscriptions, the client has the configuration of what it would like from the switch. It will connect to the switch and pull the information listed in the client subscription configuration.
* For dial-out subscriptions, the switch has the configuration of what to provide to the client. It will connect to the client and send the information listed in the switch subscription configuration.

Starting in NX-OS 9.3.1, Nexus switches support the following subscription features:

* Once
    * Collect current values only once.
* Poll
    * When the switch receives a poll message, it will send current values.
* Stream - Sample
    * Collect current values every stream interval. Supported time interval ranges are from 1 to 604800 seconds. The default sample time is 10 seconds.
* Stream - On_Change
    * Collect current values immediately. After this intiial collection, only collect values when there is a change.
* Stream - Target_Defined
    * This allows the target to define the best type of subscription to use.