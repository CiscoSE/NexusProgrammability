# Common Sensor Paths

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
| Description | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/descr |
| Presence | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fanPresent |
| Direction | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/dir |
| Status | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/operSt |
| Vendor | | /System/ch-items/ftslot-items/FtSlot-list/ft-items/fan-items/Fan-list/vendor |
| Model | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fanProdId |
| RPM | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/fanRpm |
| Fan speed (percent) | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/fanSpeed |
| Max RPM | | /System/pie-items/env-items/fan-items/fan_env_info-items/fan_env_record-items/FanEnvRecord-list/fan_params-items/FanParams-list/maxRpm |

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

## Interface
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Interface counters | 	/interfaces/interface/state/counters | 	/System/intf-items/phys-items/PhysIf-list/dbgEtherStats-items |
| Admin status | /interfaces/interface/state/admin-status | |
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

## BGP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## OSPF
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## ISIS
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

## LACP
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

## VLAN
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| VLAN ID | /network-instances/network-instance/vlans/vlan/state/vlan-id | |