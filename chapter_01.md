# TCP / IP

**TCP/IP** model by **DARPA** *(Defense Advanced Research Projects Agency)*.
**OSi** *(open systems interconnection)* model by **ISO** *(international standards organization)*.


**RFC** *(request for comment)* documents define protocols.
**RFC** does not redefine already defined protocols. (ie, **RFC** just references the LAN definition by **IEEE**)

> TCP/IP model is considered the more practical model of the two.

![TCP/IP vs OSI](/images/networking_models.png)

TCP provides error recovery services.

4 steps of data transmission.

1. Encapsulation
2. Transmission
3. Recieving
4. De-Encapsulation

## Encapsulation

Data is encapsulated on each layer.

![Encapsulation](/images/osi_encapsulation.png)

> Encapsulation standards in the OSi model is different than that of TCP/IP.

![Encapsulation](/images/osi_pdu.png)

---

## PROTOCOLS

![Protocols](/images/protocols.png)

---

### ROUTING PROTOCOLS

---

**INTERIOR GATEWAY PROTOCOLS (IGPs)**

> Used with-in an autonomous system ( Company’s / ISP’s network ).

* Distance-vector protocols
    - ***RIP (Routing Information Protocol)***
    - ~~RIPng (RIP next generation for IPv6)~~
    - ~~IGRP (Interior Gateway Routing Protocol, Cisco-proprietary, obsolete)~~

* Advanced distance-vector / hybrid
    - ***EIGRP (Enhanced IGRP, Cisco-proprietary)***

* Link-state protocols
    - ***OSPFv2 (Open Shortest Path First for IPv4)***
    - ~~OSPFv3 (OSPF for IPv6)~~
    - ***IS-IS (Intermediate System to Intermediate System, supports IPv4/IPv6)***

**EXTERIOR GATEWAY PROTOCOLS (EGPs)**

> Used in between autonomous systems.

* ***BGP (Border Gateway Protocol)***
* ~~BGP-4 (current standard, supports IPv6 as MP-BGP, Multiprotocol BGP)~~
* ~~EGP (the original Exterior Gateway Protocol, now obsolete)~~

---

### LAN PROTOCOLS

---
~~
* ~~Ethernet (IEEE 802.3) / Fast Ethernet / Gigabit Ethernet~~
    - ~~Ethernet over twisted pair *( 10BASE-T, 100BASE-TX, 1000BASE-TX )*~~
    - ~~Ethernet over fiber *( 100BASE-FX, 1000BASE-LX )*~~

* Wireless LAN Protocols (IEEE 802.11)
    - Wi-Fi (802.11a/b/g/n/ac/ax/be)

* Bridging / Switching / Spanning
    - ***Spanning Tree Protocol (STP, IEEE 802.1D)***
    - ***Rapid STP (RSTP, IEEE 802.1w)***
    - ***Multiple STP (MSTP, IEEE 802.1s)***
    - ***VLAN protocols (IEEE 802.1Q) + Trunking***

* Control & Management Protocols in LANs
    - ***LLDP (Link Layer Discovery Protocol, IEEE 802.1AB)***
    - ***CDP (Cisco Discovery Protocol, proprietary)***
    - ***LACP (Link Aggregation Control Protocol, IEEE 802.1AX)***

---

### WAN PROTOCOLS

---

* ***HDLC (High-Level Data Link Control)***
* ***PPP (Point-to-Point Protocol)***
* ***MPLS (Multiprotocol Label Switching)***
