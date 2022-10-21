# Common Sensor Paths

## System General
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

## System Hardware - Power Supply
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| ID number | | /System/ch-items/psuslot-items/PsuSlot-list/id |
| Physical ID number | | /System/ch-items/psuslot-items/PsuSlot-list/physId |
| Description | | /System/ch-items/psuslot-items/PsuSlot-list/descr |
| Slot type | | /System/ch-items/psuslot-items/PsuSlot-list/type |
| Presence | | /System/ch-items/psuslot-items/PsuSlot-list/operSt |
| Location | | /System/ch-items/psuslot-items/PsuSlot-list/loc |
| State | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/operSt |
| Current draw | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/drawnCurr |
| Source voltage | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/vSrc |
| PSU voltage | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/volt |
| Fan state | | /System/ch-items/psuslot-items/PsuSlot-list/psu-items/fanOpSt |

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

## Platform
| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |

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