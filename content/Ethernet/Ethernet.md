---
aliases:
  - Enterprise access networks
tags:
  - protocol
---
Enterprise access networks (Ethernet):
- A [Link Layer](OSI%20layers/Link%20Layer/Link%20Layer.md) protocol
- Typically used in companies, universities, etc.
- 10 Mbps, 100Mbps, 1Gbps, 10Gbps transmission rates
- Today, end systems typically connect into Ethernet switch
- Ethernet is **connectionless** and **unreliable**

Uses [CSMA/CD](OSI%20layers/Link%20Layer/CSMA.md):
- Carrier Sense: Wait for link to be idle
	- Channel idle: start transmitting
	- Channel busy: wait until idle
	- A strategy is p-persistent if, after waiting for the line to clear, the sender sends with probability <=1
- Collision Detection: listen while transmitting
	- No collision: transmission is complete
	- Collision: abort transmission, and send jam signal
- Random Access: exponential backoff
	- After collision, wait random time before trying again
	- After $m$th collision, choose $k$ randomly from $\{0, ..., 2^{m-1}\}$ and wait for $512k$ bit times before trying again

## Star Topology

Star topology helps avoid collisions
- With a hub at the center, can have collisions
- But not with a [Switch](OSI%20layers/Link%20Layer/Switches.md) at the center
	- Separates the collision domain
	- Switch knows about the link layer protocol, smart enough not to simultaneously repeat two signals
	- Buffers simultaneous packets sent to a host
