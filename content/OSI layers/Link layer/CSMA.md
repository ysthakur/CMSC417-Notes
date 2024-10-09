---
aliases:
  - Carrier Sense Multiple Access
  - CSMA/CD
---
CSMA is a [Multi-Access Protocol](OSI%20layers/Link%20layer/Multi-Access%20Protocol.md)

Carrier Sense Multiple Access (CSMA) is like human conversation:
- Carrier sense:
	- Listen before speaking and don't interrupt
- Collision detection:
	- Detect simultaneous talking and shut up
- Random access:
	- Wait for a random period of time before trying to talk again
	- $p$-persistent CSMA - if channel is idle, transmit the frame with probability $p$

But collisions can still occur
- Wasted transmissions

## Collision Detection

The "CD" part of CSMA/CD
- Collision happens when two packets overlap at receiver

> [!note]
> [Ethernet](Ethernet/Ethernet.md) does collision detection, but not [WiFi](Wireless/Wi-Fi/WiFi.md)

Worst-case scenario of collision:
- Two farthest nodes in the LAN
- Transmission time should be greater than or equal to `2 * propagation time` for CSMA/CD to work
- Formula for minimum packet size (P) or maximum length (L):
	- $2L/c = 2d = P/B$, where $c$ is the speed of propagation

![What happens on collision](OSI%20layers/Link%20layer/csma-cd-collision.png)

- When receiver detects collision
	- Stop sending
	- Send jamming signal to ensure collision detection by all nodes in the link

## CSMA for [WiFi](Wireless/Wi-Fi/WiFi.md)

802.11 does Collision Avoidance, but cannot do Collision Detection because of these two problems:
1. Cannot detect all collisions
	- Hidden terminal problem
		- Happens because 802.11 uses physical carrier sensing, which is susceptible to the hidden terminal problem
		- [Virtual Carrier Sensing](OSI%20layers/Link%20layer/Virtual%20Carrier%20Sensing.md) can help with that
	- Signal strength fades over distance
	- (see [WiFi Broadcast Limitations](Wireless/Wi-Fi/WiFi%20Broadcast%20Limitations.md) for more info)
2. Cannot listen while sending
	- Strength of received signal is much smaller
	- Expensive to build hardware that detects collisions
