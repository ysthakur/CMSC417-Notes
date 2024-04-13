---
aliases:
  - Carrier Sense Multiple Access
---
A [Multi-Access Protocol](Multi-Access%20Protocol.md)

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

- Collision happens when two packets overlap at receiver

==TODO see notes on preparing for worst-case scenario for collision (end of lecture 18 and midway through lecture 19)==

- `Transmission time >= 2 * propagation time`

- When receiver detects collision, sends jamming signal to ensure collision detection by both senders

