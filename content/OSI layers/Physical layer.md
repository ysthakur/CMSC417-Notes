---
tags:
  - osi-layer
---
Transmission of raw bits over a communication link

## Repeaters

- Used for solving distance limitation in LANs
	- Electrical signal becomes weaker as it travels, imposing limit on length of LAN
- Repeaters join LANs together
	- Analog electrical device
	- Continuously monitors electrical signals
	- Transmits an amplified copy

## Hubs

- Joins multiple input lines electrically
	- Designed to hold multiple line cards
	- Unlike repeater, does not (necessarily) amplify signal
- Unlike repeater, hub is not analog and does not just repeat the signal
	- Regenerates signal, so noise gets removed

![Hubs](hubs.png)

## Limitations of Repeaters and Hubs

- One large shared link
	- Each bit is sent everywhere
	- So aggregate throughput is limited
- Cannot support multiple LAN technologies
	- Does not buffer or interpret frames
	- Can't interconnect between different rates/formats
- Limitations on maximum nodes and distances
	- Shared medium imposes length limits
	- e.g. can't go beyond 2500 meters on Ethernet
