---
aliases:
  - Data link layer
tags:
  - osi-layer
---
- Data transfer between neighboring network elements
- e.g. [Ethernet](Ethernet.md), 802.11 ([WiFi](../../WiFi.md)), [PPP](../../PPP.md)
- Collects a stream of bits into a larger aggregate called a [frame](Frame)
- Network adapters, along with device drivers in OS implement the protocol in this layer
- [Frames](../../Frame.md) are actually delivered to hosts

## Link Layer Responsibilities

- Single-hop addressing (e.g. Ethernet addresses)
- Media access control: [Multi-Access Protocol](Multi-Access%20Protocol.md)
	- Link-layer congestion control
	- Collision detection/collision avoidance
- Single-hop acknowledgments
	- [Automatic Repeat reQuest (ARQ)](../../ARQ.md)
	- Flow control
	- Not implemented in wired LAN (e.g. [Ethernet](Ethernet.md))
