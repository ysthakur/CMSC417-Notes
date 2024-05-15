---
tags:
  - hide
---
## Networks Overview

### Basic components of a computer network

### Interconnection, internets, the Internet

### Importance and challenges of computer networks

### Network architecture, abstractions, and protocol stacks/layers

### Resource sharing, [Circuit switching](OSI%20layers/Link%20Layer/Circuit%20switching.md), and [Packet switching](OSI%20layers/Link%20Layer/Packet%20switching.md)

- Circuit switching has a dedicated channel for each connection
- Circuit switching is better for real-time applications
- But packet switching does better resource sharing among a large number of hosts
	- Can't make circuit for every single connection
	- Circuit switching doesn't allow multitasking (can only connect to one website at a time)

### [Network edge](Network%20edge.md) and [Network core](Network%20core.md)

### Access networks

### [Failures](Failures.md), [Delay](Delay.md), [Throughput](Throughput.md), [Bandwidth](Bandwidth.md), Delay x Bandwidth

- [Bandwidth vs Throughput](Bandwidth%20vs%20Throughput.md)

## Routing Protocols

### Network as a graph

### [Distance Vector Routing](OSI%20layers/Network%20Layer/Routing/Distance%20Vector%20Routing.md)

- Uses Bellman-Ford

### [Link State Routing](OSI%20layers/Network%20Layer/Routing/Link%20State%20Routing.md)

- Each node sends Link State Packets (LSPs)
	- Packet contains information about the node's neighbor
	- Has a sequence number that tells you which LSP is newer
- Each node separately gets an idea of the entire network's topology to calculate the best path
- Makes routing loops much less likely than DV routing

==todo take notes on count-to-infinity and split horizon and poison reverse (on exam 1, q2.2)==

## [IP](IP/IP.md)

### Data plane and control plane

- Control plane: Part of network that determines how packets are forwarded
- Data plane (aka forwarding plane): Part of network that actually forwards packets

### IP Datagram Format

### Fragmentation and reassembly

- Links have a max packet length they can handle (MTU = Max Transmission Unit)
- So, need to fragment packets
- Packet identifier tells you which packet each fragment belonged to
- Fragment offset field tells you where in the packet each fragment was
- MF (More Fragments) flag tells you whether the fragment is the last one

### [IP Addresses](IP/IP%20Addresses.md)

### IP datagram forwarding

### [Subnetting](IP/Subnets.md)

### [CIDR](IP/CIDR.md)

Classless Inter-Domain Routing
- Variable length network prefixes
- `/N` means network prefix size is `N`
	- `/8` for class A
	- `/16` for class B
	- `/24` for class C

Expect problem-solving questions

==TODO look at question 2 on midterm 2 on multihoming==

### [ARP](../ARP.md) (Section 3.2.6)

- Address Resolution Protocol
- Each node creates an ARP table mapping [IP Address](IP/IP%20Addresses.md) to [MAC Address](OSI%20layers/Link%20Layer/MAC%20Address.md)
- Entries time out after a while
- Nodes create their own ARP tables without intervention from an administrator

### [DHCP](../DHCP/DHCP.md) (Section 3.2.7)

- Lets you dynamically get the following from a server:
	- IP address (main point of DHCP)
	- Address of first-hop router
	- Name and IP of [DNS](DNS/DNS.md) server
	- Network mask
- Each network must have at least one DHCP server or DHCP relay agent

### Private address spaces and [NAT](../NAT.md)

- NAT (Network Address Translation) translates between public and private IP addresses

### [ICMP](../ICMP/ICMP.md) (Section 3.2.8; Ping and Traceroute in class slides)

- A collection of error messages that are sent back to source host if a router or host is unable to process an IP datagram successfully

- [Ping](../ICMP/Ping.md) - Use ICMP echo messages
- [Traceroute](../ICMP/Traceroute.md) - Sends packets with small TTLs so each router sends an ICMP Time Exceeded error message back

Expect problem solving type questions on ICMP and Traceroute

### [VPN](../VPN.md)s and Tunnels (Section 3.2.9)

- Packet is encapsulated (and encrypted) at Gateway A and decapsulated (and decrypted) at Gateway B

### Basics of [IPv6](IP/IPv6.md)
==TODO IMPORTANT==

Main differences from IPv4:
- Has unicast, anycast, and multicast, no broadcast
- No header checksum (left for application layer)
- No fragmenting - if packet exceeds MTU, it's dropped

### Problem solving for

1. Network delay, throughput, bandwidth
2. IP addresses and subnetting
3. IP fragmentation and reassembly
4. Routing protocols

## [Transport Layer](OSI%20layers/Transport%20Layer.md) multiplexing and demultiplexing
## [UDP](UDP.md)

- Connectionless
- Provides:
	- Checksum
	- Multiplexing based on IP address and port number

## [TCP](TCP/TCP.md) (Chapter 5)

- [TCP Handshake](TCP/TCP%20Handshake.md)
	- Used for exchanging ISN

==TODO know how to calculate advertised window for problem solving questions==
Advertised window:
- How many bytes receiver has available in buffer
- Receiver sends in header of ACK messages and during handshake
- If sender receives 0 window size, periodically sends 1-byte messages to test if receiver window has increased in the meantime

### Reliable byte stream (Section 5.2)

### Packet format, flags, sequence number (Section 5.2.2, 5.2.3)

### [ARQ](../ARQ/ARQ.md) protocols: [Stop and Wait](ARQ/Stop%20and%20Wait.md), [Sliding Window](ARQ/Sliding%20Window.md) (Section 5.2.4 and class slides)

Stop-and-wait:
- Wait for an ACK before sending out the next packet
- Really sucky, sliding window is better

Sliding window:
- Choose a window of size N
- Send out N packets at once
- When you receive an ACK, you can move the window forward by 1
- Two ways to deal with packet loss:
	- Go-back-N: retransmit the lost packet and every packet after it (in the window)
	- Selective repeat/selective retransmit: only retransmit lost packets

==TODO learn how to calculate throughput for these two==

### [Cumulative ACK](TCP/Cumulative%20ACK.md) (Section 6.3.2, 6.3.3, class slides)
==TODO important==

### [TCP Flow Control](TCP/TCP%20Flow%20Control.md) (Section 5.2.4)
==TODO important==

### [Silly window syndrome](TCP/Silly%20window%20syndrome.md), [Nagle's algorithm](TCP/Nagle's%20algorithm.md) (Section 5.2.5)

- Suppose a receiver has a really small window
- Packets have a minimum size due to header
- Sender sends a packet, window gets smaller, receiver advertises a smaller window
- Sender sends a smaller packet, window gets even smaller
- And so on, until the window hits 0 and the actual message is smaller than the header
- Very inefficient
- **Nagle's algorithm** reduces the number of small TCP packets (sender-side solution)
- **Delayed ACK** is a receiver-side solution

### Karn-Partridge Algorithm (Section 5.2.6)

- Used to help estimate RTT more accurately
- Three rules:
	1. Stop taking RTT samples when TCP retransmits
	2. Start again after a regular transmission/reception
	3. Each time TCP retransmits, set next timeout to be twice the last timeout value
- Problem with rules #1 and #2 if delay increases sharply:
	- TCP would ignore RTT of all retransmitted packets
	- Estimated RTT may never be updated
	- Then TCP will continue retransmitting every segment

### [Congestion Control](TCP/Congestion/TCP%20Congestion.md) (Chapter 6)

==TODO important, get better understanding==

- TCP detects congestion through packet loss
	- And packet loss is detected using timeouts or 3 duplicate ACKs

==TODO check out the congestion window graph in midterm 2 (question 5)==

**AIMD protocol** (Section 6.3.1)

**Drop-tail FIFO queue** (Section 6.2.1)
- See [Queue Management](TCP/Queue%20Management/Queue%20Management.md)

**[Slow start](TCP/Congestion/Slow%20start.md)** (Section 6.3.2)

**[Fast Retransmit + Fast Recovery](TCP/Fast%20Retransmit%20+%20Fast%20Recovery.md)** (Section 6.3.3)

- Fast retransmit: When 3 DUP ACKs received, retransmit lost packet without waiting for timeout
- Fast recovery: When fast retransmit is triggered, instead of going into [Slow start](TCP/Congestion/Slow%20start.md), just halve CWND

**[TCP Variants](TCP/TCP%20Variants.md) and [Router-Assisted Congestion Control](TCP/Congestion/Router-Assisted%20Congestion%20Control.md)** (Chapters 5 and 6)

**[TCP Vulnerabilities](TCP/TCP%20Vulnerabilities.md)** (Mentioned research paper and class slides)

Problem solving questions on:
1. 3-way handshake for TCP
2. Calculating header fields for TCP segments/packets and ACKs
4. Observing congestion window behavior

## Link layer protocols (Chapters 2, 3, 4)

### Types of links

### Link layer address, [ARP](ARP.md)

### Medium access protocols, [CSMA](OSI%20layers/Link%20Layer/CSMA.md)

### [Ethernet](Ethernet/Ethernet.md): Architecture, medium access ([CSMA/CD](OSI%20layers/Link%20Layer/CSMA.md))

### Repeater, hubs, [Switches](OSI%20layers/Link%20Layer/Switches.md), [Bridges](OSI%20layers/Link%20Layer/Bridges.md), Routers

### [Wireless Access Networks](Wireless%20Access%20Networks.md), [WiFi](Wireless/Wi-Fi/WiFi.md) protocol

- BSS: Basic Service Set

### [Mobility](Wireless/Mobility.md) in wireless networks

## Intra-AS routing and Inter-AS routing, [BGP](Inter-Domain%20Routing/BGP.md)

## Security issues in BGP networks

## Application layer protocols

### Architecture

### [DNS](DNS/DNS.md)

### Web and [HTTP](HTTP/HTTP.md)

### [Email](Email/Email.md)

## Problem-Solving type questions

- Ethernet, CSMA/CD
- Wireless channel sharing
- Learning bridge, repeater, hub, switch, and router
- BGP protocol and attacks
- [DNS](DNS/DNS.md)

## Stuff for cheat sheet

- ARQ utilization formulas
- IP address classes (A, B, C)
- 
