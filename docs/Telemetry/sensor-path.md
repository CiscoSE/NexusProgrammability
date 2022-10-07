# Common Sensor Paths

## System

| Metric      | Openconfig Model | Native Model |
| :--- | :--- | :--- |
| Memory utilized | /components/component/state/memory/utilized | |

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

