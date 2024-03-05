---
aliases:
  - Internet Control Message Protocol
---
Internet Control Message Protocol (ICMP)
- Defines a collection of error messages that are sent back to the source host whenever a router or host is unable to process an IP datagram successfully, for example:
	- Destination host unreachable due to link/node failure
	- Reassembly process failed
	- TTL had reached 0 (so datagrams don't cycle forever)
	- IP header checksum failed
- ICMP-Redirect
	- From router to a source host
	- With a better router information

