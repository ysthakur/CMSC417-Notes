---
aliases:
---
From [Past Exams/s21-0.pdf](Past%20Exams/s21-0.pdf)

## Nomenclature

- Autonomous system: ==TODO==
- [CIDR](IP/CIDR.md): Classless Inter-Domain Routing
- Multi-homed AS: ==TODO==
- Poisoned Reverse: ==TODO==
- Selective ACK (SACK): ==TODO==

## Routing

#### List two advantages of [Link State Routing](OSI%20layers/Network%20layer/Routing/Link%20State%20Routing.md) over [Distance Vector Routing](OSI%20layers/Network%20layer/Routing/Distance%20Vector%20Routing.md)
==TODO==

#### Give an example that shows the difference between regular Distance Vector (DV) and DV with Split Horizon
==TODO==

#### How is TTL as used in Link State Routing different from IPv4?
==TODO==

#### What is a “triggered update” in Distance Vector. Are they necessary? Why or why not?
==TODO==

## Internet Protocol

### Suppose you are allocated the prefix 44.100.101.0/23
1. How many IP addresses do you control? $2^9 = 512$
2. Divide your allocation into three subnets, two of equal size and one double the size of the others. For each subnet, list the following:
==TODO check this==

|  | Subnet ID | Mask | Broadcast | # hosts | Lowest address | Highest address |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Subnet 0 | 44.100.100.0/25 | 255.255.255.128 | ==TODO== | 128 | 44.100.100.0 | 44.100.100.127 |
| Subnet 1 | 44.100.100.128/25 | 255.255.255.128 | ==TODO== | 128 | 44.100.100.128 | 44.100.100.255 |
| Subnet 2 | 44.100.101.0/24 | 255.255.255.0 | ==TODO== | 256 | 44.100.101.0 | 44.100.101.255 |

### Suppose a IP fragment with ID 1023, offset 128, MF=1, DF=0, TTL=17 and payload size 532 bytes is transmitted on a link with MTU 276 bytes. List the header values for the resultant fragments.

You may assume no IP options; IP Len includes header. You may assume that link
MTU of x means an IP datagram of total length x can be sent over the link

==TODO==

|  | IP ID | Offset | MF | DF | TTL | IP Len |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Fragment 0 |  |  |  |  |  |  |
| Fragment 1 |  |  |  |  |  |  |
| Fragment 2 |  |  |  |  |  |  |

### IP reassembly code receives a datagram with previously unseen Identification=417, Total Len 1044 bytes, MF flag=1, and offset=8191. How should this datagram be processed?

## [CIDR](IP/CIDR.md), BGP

### What is the difference between a stub and a transit AS?
Not covered.

### Provider P has four customers with allocations 112.8.32/24, 112.8.33/24, 112.8.34/24, and 112.8.35/24. What CIDR prefix should P advertise?

112.8.32/24

### UMD has two providers, Cogent and Internet2. Internet2 only advertises prefixes from academic institutions. What techniques can can UMD use to ensure that all outgoing traffic to academic institutions is carried by Internet2?
Not covered?

### UMD wants to run a remote campus in Lyon, France with address allocation 128.8.10/24. What prefixes and AS numbers should be advertised from College Park and Lyon?
Not covered.

## Mobile IP, Implementation

Not covered.
