# WAN

**WAN** defines physical ( *layer1* ) and datalink ( *layer2* ) protocols for long distance communications.

![WAN](/images/wans.png)

**LEASED LINE WAN**

![WAN](/images/leased_line.png)

**ETHERNET WAN**

![WAN](/images/ethernet_wan.png)

| Feature                       | **Leased Line**                                     | **Circuit-Switched WAN**                                                   | **Packet-Switched WAN**                                                  | **Internet VPN (Overlay)**                                           |
| ------------------------------| --------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| **Connection Type**           | Dedicated point-to-point link                       | Temporary connection established per call/session (like old ISDN, dial-up) | Virtual circuits across shared provider network (Frame Relay, ATM, MPLS) | Logical tunnel over public Internet (IPsec, GRE, SSL VPN, WireGuard) |
| **Bandwidth**                 | Fixed, guaranteed, symmetric                        | Fixed per session, usually low                                             | Shared, but provider can guarantee certain levels (QoS)                  | Variable, depends on Internet link speed and congestion              |
| **Typical Speed**             | T1/E1: 1.5/2 Mbps; T3/E3: 45 Mbps; up to Gbps+ on fiber | ISDN BRI: 128 Kbps, PRI: up to 2 Mbps; dial-up: 56 Kbps   | Frame Relay: 56 Kbps – 45 Mbps; ATM: up to 622 Mbps; MPLS/Metro Ethernet: 10 Mbps – multi-Gbps | From home broadband speeds (50 Mbps–1 Gbps) to enterprise fiber (multi-Gbps); VPN overhead reduces throughput slightly |
| **QoS (Quality of Service)**  | Guaranteed (dedicated line)                             | None (best effort)                                        | Supported in MPLS/ATM (service classes)                                                        | Limited—depends on Internet + SD-WAN tricks                                                                            |
| **Scalability**               | Poor (point-to-point only, hub-and-spoke costs explode) | Poor (temporary links, no mesh scaling)                   | Good (multiple sites over shared provider cloud)                                               | Very good (any site with Internet can join VPN)                                                                        |
| **Cost**                      | $$$$ (most expensive)                                   | $ (cheap, legacy)                                         | $$–$$$ (cheaper than leased lines, MPLS can be pricey)                                         | $ (lowest cost, just Internet bandwidth)                                                                               |
| **Security**                  | High (private, no sharing)                              | Low (clear-text unless encrypted)                         | Moderate (provider isolation, but not fully private)                                           | High if using strong encryption (IPsec, WireGuard)                                                                     |

---

## HDLC

![WAN](/images/hdlc.png)

![WAN](/images/hdlc_frame.png)

![WAN](/images/hdlc_frames.png)

1. I-Frames (Information Frames) : Carry actual data and for error and flow control.

2. S-Frames (Supervisory Frames) : Control, acknowledgement and error-handling frames.

3. U-Frames (Unnumbered Frames) : Management and special cases. no sequence numbers. establishing / closing connections, exchanging commands like “reset,”.

---

## PPP

- Layer: Works at the Data Link layer.
- Encapsulation: Wraps packets into a standard format for transmission over point-to-point links.
- Multiprotocol: Thanks to its Protocol field, PPP can carry different network layer protocols simultaneously.
- Extensible: It uses subprotocols for extra duties, like authentication and compression.

![WAN](/images/ppp_session.png)

1. Link establishment phase: In this phase, each PPP device sends LCP packets to configure and test the data link
2. Authentication phase (optional): If authentication is enabled, either PAP or CHAP will be used.
3. Network layer protocol phase: PPP sends NCP packets to choose and configure Network Layer protocol (OSI Layer 3) to be encapsulated and sent over the PPP data link

![WAN](/images/ppp.png)

- Flag (01111110): Marks beginning/end of frame.
- Address: Always set to broadcast (11111111), since it’s point-to-point anyway.
- Control: Usually 00000011, meaning "unnumbered frame" (PPP doesn’t bother with sequence numbers).
- Protocol: Says what’s inside the Data field (e.g., 0x0021 = IPv4, 0x0057 = IPv6).
- Data: The payload.
- FCS (Frame Check Sequence): Error checking via CRC.

---

**PAP**

![WAN](/images/pap-authentication.png)

**CHAP**

![WAN](/images/chap-authentication.png)
