---
tags:
  - protocol
aliases:
  - User Datagram Protocol
---

User Datagram Protocol (UDP) is a [transport layer](OSI%20layers/Transport%20layer.md) protocol
- Bare minimum transport protocol
- "Best effort" service, UDP segments may be lost or delivered out of order
- Connectionless:
	- No handshaking between UDP client and server
	- Each UDP segment handled independently of others
- Datagram messaging service
	- Demultiplexing based on port numbers
	- Detects corruption using checksum
- To achieve reliable transfer over UDP, add reliability at application layer
	- Application-specific error recovery

Uses for UDP:
- Streaming multimedia apps
- Simple query-response protocols:
	- [DNS](DNS.md)
	- [DHCP](DHCP/DHCP.md)

## Advantages of UDP

- Fine-grained control: UDP sends as soon as the application writes
- No connection set-up delay
- No connection state: No buffers, parameters, sequence numbers, etc.
- Small header overhead: UDP header only 8 bytes

## Checksum

Goal: detect "flipped bits" in transmitted segment

To compute:
- Treat segment contents as sequence of 16-bit numbers
- Checksum is 1's complement sum of segment contents

Receiver checks if computed checksum equals checksum field value