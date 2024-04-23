---
aliases:
  - Data link layer
tags:
  - osi-layer
---
- Data transfer between neighboring network elements
- e.g. [Ethernet](Ethernet/Ethernet.md), 802.11 ([WiFi](WiFi/WiFi.md)), P2P/PPP
- Collects a stream of bits into a larger aggregate called a [frame](Frame)
- Network adapters, along with device drivers in OS implement the protocol in this layer
- [Frames](../../Frame.md) are actually delivered to hosts

> [!tip]
> At the link layer, everything is a broadcast, and unicast is only an illusion.

## Link Layer Responsibilities

- Single-hop addressing (e.g. Ethernet addresses)
- Media access control: [Multi-Access Protocol](Multi-Access%20Protocol.md)
	- Link-layer congestion control
	- Collision detection/collision avoidance
- Single-hop acknowledgments
	- [Automatic Repeat Query](../../ARQ/ARQ.md) (ARQ)
	- Flow control
	- Not implemented in wired LAN (e.g. [Ethernet](Ethernet/Ethernet.md))
