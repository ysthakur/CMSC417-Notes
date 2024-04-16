---
aliases:
  - Automatic Repeat Query
  - Automatic Repeat Request
---
ARQ (Automatic Repeat Query, a.k.a. Automatic Repeat reQuest) is an error-control method to ensure reliable data transmission (used by [TCP](../OSI%20layers/Transport%20layer/TCP/TCP.md))

- Uses ACK messages and timeouts
- Receiver sends ACK when it receives packet
- Sender waits for ACK and times out

Two variations:
1. [Stop and Wait](Stop%20and%20Wait.md)
	- Simplest ARQ protocol
	- Send a packet, stop and wait until ACK arrives
	- Not used as much anymore because sliding window is better
	- Stop-and-wait is inefficient:
		- Only one TCP segment is "in flight" at a time
		- Very bad for application with high delay and bandwidth
2. [Sliding Window](Sliding%20Window.md)
