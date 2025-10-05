# ETHERNET

**Ethernet** refers to a family of **LAN** standards that define physical and datalink layers by IEEE.

## SMALL OFFICE / HOME OFFICE (SOHO) LAN

![LAN COMPONENTS](/images/network.png)

| Router | Switch | Access Point |
| -------- | ------- | ------- |
| Operate at Layer 3 (Network)  | Operate at layer two (Data Link Layer)  | Operate at layer two (Data Link Layer) |
| Maintains IP address in the routing table | Maintains MAC address in a lookup table | Maintains MAC address in a lookup table |
| Wired or Wireless | Wired | Wireless |

## ROUTER VS GATEWAY

![ROUTER VS GATEWAY](/images/router.png)

| Router | Gateway |
| -------- | ------- |
| Can only work with similar networks  | Can work with dissimilar networks |
| Using TCP/IP and UDP protocols | Using different protocols |
| Routes data packet from one network to another based on internal routing tables | Converts the data packets protocols from one format to another |

## ETHERNET STANDARDS (802.3)

> T - Electrical (around 100m)\
> LX - Fiber Optics (around 5km)

| Speed | Name | Code | Standard |
| -------- | ------- | ------- | ------- |
| 10 Mbps | Ethernet | 10BASE-T | 802.3 |
| 100 Mbps | Fast Ethernet | 100BASE-T | 802.3u |
| 1000 Mbps | Gigabit Ethernet | 1000BASE-T | 802.3ab |
| 1000 Mbps | Gigabit Ethernet | 1000BASE-LX | 802.3z |
| 10 Gbps | 10 Gig Ethernet | 10GBASE-T | 802.3an |

## CABLE STANDARDS

![SINGLE TWISTED PAIR](/images/twistedpair.png)

10BASE-T / 100BASE-T (2 pairs) 4 wires\
1000BASE-T (4 pairs) 8 wires

**RJ-45** connector has 8 pins.\
devices use standard encoding schemes to communicate, ie, 10BASE-T uses 1/10^7 second intervals for bits.\
twisting the cables help cancel out electro magnetic inteference.(crosstalk).\

**DEVICES USE STANDARD PINS TO SEND AND RECIEVE DATA**

![pc](/images/pc.gif)


![sw](/images/sw.gif)


**SUITABLE CABLE TYPE MUST BE USED ACCORDING TO THE DEVICES THAT ARE CONNECTED TO EITHER END OF THE CABLE.**

> ie, PC to PC connection require **Crossover cable** as both send data on pins 1/2 and recieve data on pins 3/6 

![st](/images/pctosw.gif)

> ie, PC to Switch connection require **Straight Through cable** as PC send data on pins 1/2 and Switch recieves data on pins 1/2

![co](/images/pctopc.gif)

![co](/images/pctopc2.gif)

some switches have **AUTO-MDIX** which can detect wrong cable type and adapt it's logic accrodingly.

![stco](/images/straight_crossover.png)

**FIBER CABLES**

![fo](/images/fiber_cable.png)

![fo](/images/multimode-and-singlemode.png)

---

## ETHERNET FRAME

![et](/images/Ethernet-Frame.png)

* Preamble : syncronization
* SOF : start of frame delimiter
* Type : protocol
    - IPv4 [0800]
    - IPv6 [86DD]
* FCS : error detection
    - Errored frame will be discarded.
    - TCP protocol must notice the discard to re-attempt.

> According to IEEE 802.3 frame must be **46 - 1500**, anything less will be **padded**.

* Half-Duplex : devices can only send ***or*** recieve data at once.
    - use **Carrier Sense Multiple Access** + **Collision Detection** (CSMA/CD)
* Full-Duplex : devices can send ***and*** recieve data at once.

---

## TCP/IP PACKET

![ip](/images/tcp.png)

---

## UDP/IP PACKET

![ip](/images/udp.png)

---

## ENCAPSULATION

![ip](/images/tcp_pdus.png)

---

## DELIVERY METHODS

![dm](/images/delivery_mode.png)

---
