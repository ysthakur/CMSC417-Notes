---
aliases:
  - Internet Control Message Protocol
---
Internet Control Message Protocol (ICMP) defines a collection of error messages that are sent back to the source host whenever a router or host is unable to process an [IP](OSI%20layers/Network%20Layer/IP/IP.md) datagram successfully.

Examples of error messages:
- Destination host unreachable due to link/node failure
- Reassembly process failed
- TTL had reached 0 (so datagrams don't cycle forever)
- IP header checksum failed

ICMP Redirect Message:
- From router to a source host
- With a better router information

Provides basis for two debugging tools:
- [Ping](Ping.md)
- [Traceroute](Traceroute.md)
