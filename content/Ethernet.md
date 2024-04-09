---
aliases:
  - Ethernet
  - Enterprise access networks
tags:
  - protocol
---
- Enterprise access networks (Ethernet)
- Typically used in companies, universities, etc.
- 10 Mbps, 100Mbps, 1Gbps, 10Gbps transmission rates
- Today, end systems typically connect into Ethernet switch

Uses CSMA/CD:
- Carrier Sense: Wait for link to be idle
	- Channel idle: start transmitting
	- Channel busy: wait until idle
	- A strategy is p-persistent if, after waiting for the line to clear, the sender sends with probability <=1
- Collision Detection: listen while transmitting
	- No collision: transmission is complete
	- Collision: abort transmission, and send jam signal
