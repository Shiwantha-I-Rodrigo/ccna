# SUBNETING

1. devices ***not seperated*** by a router must be in the ***same subnet***.
2. devices ***sepertaed*** by a router must be in ***different subnets***.

![SUB](/images/subnets.png)

---

Each,
- VLAN
- Point to Point WAN link
- Group of devices seperated by a router
- Firewall zone **\***

must reside in it's own subnet.

---

Consider,
- Hosts per subnet
- Future growth
- Design requirements (zones, etc...)
- Number of network segments

when deciding the size of subnets.

---

1. Largest subnet has 100 devices.

2 $^{H}$ - 2 > 100\
2 $^{H}$ > 102

    ```
                                                ▽
    { 1  ,  2  ,  4  ,  8  ,  16 ,  32 ,  64 , 128, 256, 512 , ... }
    { 0  ,  1  ,  2  ,  3  ,  4  ,  5  ,  6  ,  7 ,  8 ,  9  , ... }
    ```

**H = 7**

---

**CLASSFUL NETWORKS**

| **Class** | **First Octet Range** | **Default Subnet Mask** | **Networks Available**   | **Hosts per Network**    | **Special Trivia**                                                                         |
| --------- | --------------------- | ----------------------- | ------------------------ | ------------------------ | ------------------------------------------------------------------------------------------ |
| **A**     | 1 – 126               | 255.0.0.0 (/8)          | 126 (0 and 127 reserved) | ~16.7 million            | First bit is `0`. 127.x.x.x reserved for loopback. Class A was given to *very* large orgs. |
| **B**     | 128 – 191             | 255.255.0.0 (/16)       | 16,384                   | ~65,534                  | First bits `10`. Sweet spot for universities, mid-sized ISPs.                              |
| **C**     | 192 – 223             | 255.255.255.0 (/24)     | ~2 million               | 254                      | First bits `110`. Common for small LANs.                                                   |
| **D**     | 224 – 239             | N/A (Multicast)         | N/A                      | N/A                      | First bits `1110`. Reserved for multicast groups. Not for host addressing.                 |
| **E**     | 240 – 255             | N/A (Experimental)      | N/A                      | N/A                      | First bits `1111`. Reserved for experimental use. Some addresses never used publicly.      |

**PRIVATE IP RANGES**

**Class A** : 10.0.0.0 – 10.255.255.255\
**Class B** : 172.16.0.0 – 172.31.255.255\
**Class C** : 192.168.0.0 – 192.168.255.255

> Classful addressing was retired in the 90's in favour of CIDR.

---

Mitigating public IP address exhaustion,
1. IPv6 (128 bits)
2. Classless Interdomain Routing (CIDR)
3. Network Address Translation (NAT)

---

```
172.16.16.10/22
                                                      Subnet
                                                        ▽
                       22 --> 11111111  11111111  111111  00  00000000
             172.16.16.10 --> 10101100  00010000  000100  00  00001010

First address (SubnetID)  --> 10101100  00010000  000100  00  00000000  --> 172.16.16.0
 Last address (Broadcast) --> 10101100  00010000  000100  11  11111111  --> 172.16.19.255
```

* First and Last addresses must be reserved for SubnetID ( completely unusable ) and broadcast ( ARP, DHCP, etc... ).
* General recomendation is to use first or last usable address as gateway.

```
If the network ic class B
                                     Network  Subnet
                                        ▽      ▽
     First subnet --> 10101100  00010000  000000  00 00000000  --> 172.16.0.0
    Second subnet --> 10101100  00010000  000001  00 00000000  --> 172.16.3.0
      Last subnet --> 10101100  00010000  111111  00 00000000  --> 172.16.252.0
```

## Subnet Masks

- [ Dotted Decimal ] --> **255.255.255.0**
- [ Prefix ] --> **/24**
- [ Binary ] --> **11111111 11111111 11111111 00000000**

> Classless **( Prefix + Host )**\
> Classful **( NetworkID + SubnetID + Host )**

255.255.255.224  -->  11111111 11111111 11111111 11100000  --> **( VALID MASK)**\
255.255.255.225  -->  11111111 11111111 11111111 1110000***1***  --> **( INVALID MASK)**

---

## Decimal Calculations

> The concept of "number of subnets" does not exist in CIDR.\
> as there is no boundry between network and sub network segments.\
> unless both masks are specified explicitly.\
> Network --> 192.168.1.0/24\
> Subnet --> 192.168.1.0/26\
> subnetting in CIDR is essentially breaking a CIDR block into smaller blocks.

```
CLassless       <------Network-------><----Host--->

                11111111 11111111 11110000 00000000

Class A         <Network><---Subnet--><----Host--->
```

---

1. Find the Network ID of 130.4.102.1 netmask 255.255.240.0

    - from third octet --> 256 - 240 == 16 --> third octet Block size 16

    - possible subnets --> 0 , 16, 32, 48, 64, 80, **96**, **112**, 128, ...

    - 102 falls after --> 96

    - network id == *130.4.96.0*

    - 102 falls before --> 112

    - bradcast address == *130.4.111.255*

---
