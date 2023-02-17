# Common Sensor Paths

## ARP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Admin state | | /System/arp-items/inst-items/adminSt |
| Operational state | | /System/arp-items/operSt |
| Allow ARP outside subnet | | /System/arp-items/inst-items/allowStaticArpOutsideSubnet |
| Cache limit | | /System/arp-items/inst-items/cacheLimit |

## BGP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## CDP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| All CDP info | | /System/cdp-items/inst-items |
| CDP status | | /System/cdp-items/inst-items/adminSt |
| Holdtime | | /System/cdp-items/inst-items/holdIntvl |
| Interface admin state | | /System/cdp-items/inst-items/if-items/If-list/adminSt |
| Interface ID | | /System/cdp-items/inst-items/if-items/If-list/id |
| Interface VLAN | | /System/cdp-items/inst-items/if-items/If-list/nativeVlan |
| Interface status| | /System/cdp-items/inst-items/if-items/If-list/operSt |
| Port local MAC | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/localMAC |
| Port MTU | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/mtu |
| Neighbor capabilities | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/cap |
| Remote platform type | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/platId |
| Remote interface | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/portId |
| Remote MAC | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/remoteMAC |
| Remote IP | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/intf-items/IntfAddr-list/addr |
| Remote management IP | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/mgmt-items/MgmtAddr-list/addr |
| Remote device name | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/sysName |
| Remote device version | | /System/cdp-items/inst-items/if-items/If-list/adj-items/AdjEp-list/ver |

## CoPP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Admin state | | /System/copp-items/adminSt |
| Operational state | | /System/copp-items/operSt |
| Class rate limiter state | | /System/copp-items/enableFlag |
| Error code | | /System/copp-items/error |
| Profile | | /System/copp-items/profile-items/prof |

## gRPC
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Listening port | | /System/grpc-items/port |
| Keepalive timeout | | /System/grpc-items/gnmi-items/keepAliveTimeout |
| Max calls allowed | | /System/grpc-items/gnmi-items/maxCalls |
| Minimum sample interval (seconds) | | /System/grpc-items/gnmi-items/minSampleInterval |

## Interface
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Interface counters | 	/interfaces/interface/state/counters | 	/System/intf-items/phys-items/PhysIf-list/dbgEtherStats-items |
| Admin status | /interfaces/interface/state/admin-status | /System/intf-items/phys-items/PhysIf-list/adminSt |
| Interface descriptions | /interfaces/interface/state/description | |
| Interface names | /interfaces/interface/state/name | |
| Ingress packets discarded | /interfaces/interface/state/counters/in-discards | |
| Egress packets discarded | /interfaces/interface/state/counters/out-discards | |
| Ingress broadcast packets | /interfaces/interface/state/counters/in-broadcast-pkts | |
| Ingress multicast packets | /interfaces/interface/state/counters/in-multicast-pkts | |
| Ingress bytes | /interfaces/interface/state/counters/in-octets | |
| Ingress unicast packets | /interfaces/interface/state/counters/in-unicast-pkts | |
| Egress broadcast packets | /interfaces/interface/state/counters/out-broadcast-pkts | |
| Egress multicast packets | /interfaces/interface/state/counters/out-multicast-pkts | |
| Egress bytes | /interfaces/interface/state/counters/out-octets | |
| Egress unicast packets | /interfaces/interface/state/counters/out-unicast-pkts | |
| Ingress errors | /interfaces/interface/state/counters/in-errors | |
| Interface status | /interfaces/interface/state/oper-status | |
| Egress errors | /interfaces/interface/state/counters/out-errors | |
| Default layer | | /System/ethpm-items/inst-items/systemDefaultLayer |
| Default admin state | | /System/ethpm-items/inst-items/systemDefaultAdminSt |
| System jumbo MTU size (bytes) | | /System/ethpm-items/inst-items/systemJumboMtu |
| FEC Mode | | /System/intf-items/phys-items/PhysIf-list/FECMode |
| Access VLAN | | /System/intf-items/phys-items/PhysIf-list/accessVlan |
| Bundle port number | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/bdlPortNum |
| Port channel state | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/channelingSt |
| Member port flags | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/flags |
| LTL programmed | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/ltlProgrammed |
| Aggregation operational state | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/operSt |
| Summarized operational state | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/summOperSt |
| Aggregation member uptime | | /System/intf-items/phys-items/PhysIf-list/aggrmbrif-items/uptime |
| Auto negotiation status | | /System/intf-items/phys-items/PhysIf-list/autoNeg |
| Beacon status | | /System/intf-items/phys-items/PhysIf-list/beacon |
| Bandwidth parameter | | /System/intf-items/phys-items/PhysIf-list/bw |
| Alignment errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/alignmentErrors |
| Babble count | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/babble |
| Carrier sense errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/carrierSenseErrors |
| Control input unknown OP codes | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/controlInUnknownOpcodes |
| Deferred transmissions | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/deferredTransmissions |
| Excessive collisions | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/excessiveCollisions |
| FCS errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/fCSErrors |
| Frame too long count | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/frameTooLongs |
| Input pause frames | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/inPauseFrames |
| Input dribble | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/inputdribble |
| Internal MAC receive errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/internalMacReceiveErrors |
| Internal MAC transmit errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/internalMacTransmitErrors |
| Late collisions count | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/lateCollisions |
| Lost carrier errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/lostCarrierErrors |
| Multiple collision frames | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/multipleCollisionFrames |
| No carrier errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/noCarrierErrors |
| Output pause frames | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/outPauseFrames |
| Runts | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/runts |
| SQET test errors | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/sQETTestErrors |
| Single collision frames | | /System/intf-items/phys-items/PhysIf-list/dbgDot3Stats-items/singleCollisionFrames |

## ISIS
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## LACP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## LLDP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| All LLDP information | /lldp/interfaces/interface | |
| LLDP neighbor ID type | /lldp/interfaces/interface/neighbors/neighbor/state/chassis-id-type | |
| LLDP chassis ID | /lldp/interfaces/interface/neighbors/neighbor/state/chassis-id | |
| Port ID type | /lldp/interfaces/interface/neighbors/neighbor/state/port-id-type | |
| Neighbor port ID | /lldp/interfaces/interface/neighbors/neighbor/state/port-id | |
| State status and type | /lldp/interfaces/interface/neighbors/neighbor/capabilities/capability/state | |
| State status | /lldp/interfaces/interface/neighbors/neighbor/capabilities/capability/state/enabled | |

## OSPF
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## Platform
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Hostname | | /System/name |
| System Serial number | | /System/serial |
| System copyright | | /System/showversion-items/copyRight |
| BIOS version | | 	/System/showversion-items/biosVersion |
| BIOS date | | /System/showversion-items/biosCompileTime |
| NX-OS version | | /System/showversion-items/nxosVersion |
| NX-OS date | | /System/showversion-items/nxosCompileTime |
| NX-OS image filename| | /System/showversion-items/nxosImageFile |
| Kernel uptime | | /System/showversion-items/kernelUptime |
| Last reset reason | | /System/showversion-items/lastResetReason |
| Last reset OS version | | /System/showversion-items/lastResetSysVersion |
| Last reset time | | /System/showversion-items/lastResetTime |
| System alarms | | /System/alarms-items/alarm-items/Alarm-list |
| Running config != startup config | | /System/configDirty |

### Platform - Boot
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Auto copy status | | /System/boot-items/autoCopy |
| Exclude configuration status | | /System/boot-items/excludeCfg |
| Boot success status | | /System/boot-items/image-items/image_err |
| Image verification | | /System/boot-items/image-items/imageverification |
| Supervisor 1 image | | /System/boot-items/image-items/sup1 |
| Supervisor 2 image | | /System/boot-items/image-items/sup2 |
| Supervisor 1 reload image | | /System/boot-items/image-items/sup1NextReload |
| Supervisor 2 reload image | | /System/boot-items/image-items/sup2NextReload |
| POAP state | | /System/boot-items/poap |

### Platform - Power Supply
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| PSU slot ID number | | /System/ch-items/psuslot-items/PsuSlot-list/id |
| PSU slot physical ID number | | /System/ch-items/psuslot-items/PsuSlot-list/physId |
| PSU ID number | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/id |
| Serial | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/ser |
| PSU slot description | | /System/ch-items/psuslot-items/PsuSlot-list/descr |
| PSU description | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/descr |
| Slot type | | /System/ch-items/psuslot-items/PsuSlot-list/type |
| Presence | | /System/ch-items/psuslot-items/PsuSlot-list/operSt |
| Location | | /System/ch-items/psuslot-items/PsuSlot-list/loc |
| State | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/operSt |
| Vendor | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vendor |
| Model | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/model |
| Revision | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/rev |
| Software alarm state | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/softwareAlarm |
| Hardware alarm state | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/hardwareAlarm |
| Power cord presence | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/typeCordConnected |
| Amps input (actual) | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/inputCurr |
| Amps input | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/iIn |
| Amps output (actual) | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/drawnCurr |
| Amps output | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/iOut |
| Volts source | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vSrc |
| Volts input | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vIn |
| Volts output | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vOut |
| Volts PSU | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/volt |
| VDR ID | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vdrId |
| Watts input | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/pIn |
| Watts output | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/pOut |
| Fan state | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/fanOpSt |
| Fan direction | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/fanDirection |

### Platform - Storage
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Drive ID | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/id |
| Description | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/descr |
| Drive type | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/type |
| Vendor | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/vendor |
| Model | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/model |
| Revision | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/rev |
| Serial | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/ser |
| Access type | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/acc |
| Lifetime percent used | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/lifetime |
| Manufacturing time | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/mfgTm |
| Drive status | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/operSt |
| Minor alarm count | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/minorAlarm |
| Major alarm count | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/majorAlarm |
| Terabytes written | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/tbw |
| Bad blocks | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/gbb |
| Drive warning count | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/warning |
| Read error rate | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/readErrorRate |
| P/E Cycles | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/flash-items/peCycle |

### Platform - Fans
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Fan module ID | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fanId |
| Fan ID within module | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/trayInst |
| Description | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/descr |
| Presence | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fanPresent |
| Direction | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/dir |
| Status | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/operSt |
| Vendor | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/vendor |
| Model | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fanProdId |
| RPM | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/fanRpm |
| Fan speed (percent) | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/fanSpeed |
| Max RPM | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/maxRpm |

### Platform - Chassis
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Chassis description | | /System/ch-items/descr |
| All line cards | | /System/ch-items/lcslot-items/LCSlot-list |
| Line card ID | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/id |
| Line card description | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/descr |
| Line card model | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/model |
| Line card serial number | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/ser |
| Line card hardware version | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/hwVer |
| Line card revision | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/rev |
| Line card breakout factor | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/breakoutFactor |
| Line card MAC | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/macB |
| Line card MAC end | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/macE |
| Line card number of ports | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/numP |
| Line card operational state | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/operSt |
| Line card part number | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/partNumber |
| Line card power state | | /System/ch-items/lcslot-items/LCSlot-list/lc-items/pwrSt |
| Line card physical presence | | /System/ch-items/lcslot-items/LCSlot-list/operSt |
| Supervisor ID | | /System/ch-items/supslot-items/SupCSlot-list/id |
| Supervisor location | | /System/ch-items/supslot-items/SupCSlot-list/loc |
| Supervisor slot description | | /System/ch-items/supslot-items/SupCSlot-list/descr |
| Supervisor physical presence | | /System/ch-items/supslot-items/SupCSlot-list/operSt |
| Supervisor power status | | /System/ch-items/supslot-items/SupCSlot-list/poweroff |
| Supervisor CPU ID | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/id |
| Supervisor CPU vendor | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/vendor |
| Supervisor CPU model | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/model |
| Supervisor CPU architecture | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/arch |
| Supervisor CPU speed (GHz) | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/speed |
| Supervisor CPU cores | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/cores |
| Supervisor CPU cores enabled | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/coresEn |
| Supervisor CPU threads | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/cpu-items/CPU-list/thrds |
| Supervisor RAM DIMM ID | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/dimm-items/Dimm-list/id |
| Supervisor RAM total | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/dimm-items/Dimm-list/cap |
| Supervisor RAM used | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/dimm-items/Dimm-list/used |
| Supervisor temp sensors | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list |
| Supervisor temp sensor ID | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/id |
| Supervisor temp sensor type | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/type |
| Supervisor temp sensor major threshold | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/majorThresh |
| Supervisor temp sensor minor threshold | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/minorThresh |
| Supervisor temp sensor status | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/operSt |
| Supervisor temp sensor current temp | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/tempValue |
| Supervisor temp sensor temp unit | | /System/ch-items/supslot-items/SupCSlot-list/sup-items/sensor-items/Sensor-list/unit |

## QOS
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| All QOS info | /oc-qos:qos | /System/ipqos-items |
| Dynamic buffer share | | /System/ipqos-items/dynamicBufferShare |

### QOS - Input Queue
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Input queue name | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:input/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:name | /System/ipqos-items/queuing-items/policy-items/in-items/intf-items/If-list/queCmap-items/QueuingStats-list/cmapName |
| Input queue dropped packets | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:input/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:dropped-pkts  | /System/ipqos-items/queuing-items/policy-items/in-items/intf-items/If-list/queCmap-items/QueuingStats-list/dropPackets |

### QOS - Output Queue
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Interface ID | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:interface-id | Interface ID /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/name |
| All stats | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:output/oc-qos:queues/oc-qos:queue/oc-qos:state | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list |
| Class map name | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:output/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:name | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/cmapName |
| Policy map name | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pmapName |
| Current queue depth (bytes) | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/currQueueDepth |
| Dropped byte count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/dropBytes |
| Dropped packets | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:output/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:dropped-pkts | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/dropPackets |
| Ingress queue depth | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ingQDepthBytes |
| Ingress queue dropped packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ingQDropPackets |
| Transmit octets | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:output/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:transmit-octets | |
| Transmit packets | /oc-qos:qos/oc-qos:interfaces/oc-qos:interface/oc-qos:output/oc-qos:queues/oc-qos:queue/oc-qos:state/oc-qos:transmit-pkts | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/txPackets |
| Multicast queue depth | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/mcCurrQueueDepth |
| Multicast dropped bytes count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/mcDropBytes |
| Multicast dropped packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/mcDropPackets |
| Multicast transmit byte count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/mcTxBytes |
| Multicast transmit packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/mcTxPackets |
| Priority-based flow control per packet pause received count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pfcRxPpp |
| Priority-based flow control per packet pause transmitted count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pfcTxPpp |
| Priority-based flow control watchdog queue flushed packets | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pfcwdFlushedPackets |
| Priority-based flow control watchdog queue restored count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pfcwdRestoredCount |
| Priority-based flow control watchdog queue shutdown count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/pfcwdShutdownCount |
| Random detect ECN marked packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/randEcnMarkedPackets |
| QOS statistic type | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/statType |
| Transmit byte count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/txBytes |
| Unicast current queue depth (bytes) | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ucCurrQueueDepth |
| Unicast droped bytes count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ucDropBytes |
| Unicast droped packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ucDropPackets |
| Unicast transmit byte count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ucTxBytes |
| Unicast transmit packet count | | /System/ipqos-items/queuing-items/policy-items/out-items/intf-items/If-list/queCmap-items/QueuingStats-list/ucTxPackets |

## System Hardware
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Memory utilized | /components/component/state/memory/utilized | 	/System/pie-items/modules-items/module-items/Module-list/memory-items/memory_usage-items/memUsed |
| Memory reserved | /system/memory/state/reserved| |
| Memory available | /components/component/state/memory/available | /System/pie-items/modules-items/module-items/Module-list/memory-items/memory_usage-items/memFree |
| Memory total | /system/memory/state/physical | /System/pie-items/modules-items/module-items/Module-list/memory-items/memory_usage-items/memTotal |
| Component status | /components/component/state/oper-status | |
| CPU total average utilization | /system/cpus/cpu/state/total/avg | |
| CPU current utilization | /components/component/cpu/utilization/state/instant | |
| CPU state average utilization | /components/component/cpu/utilization/state/avg | |
| CPU state minimum utilization | /components/component/cpu/utilization/state/min | |
| CPU state maximum utilization | /components/component/cpu/utilization/state/max | |
| Fan speed | /components/component/fan/state/speed | |
| Fan state | /openconfig-platform:components/component/fan/state/ | |

## VLAN
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| VLAN ID | /network-instances/network-instance/vlans/vlan/state/vlan-id | |