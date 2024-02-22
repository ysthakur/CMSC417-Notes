---
aliases:
  - Classless Inter-Domain Routing
---
Improvement on [Classful Addressing](Classful%20Addressing.md)

Uses **variable length subnet masking** - network prefixes have variable length

Example: /8 means the network prefix size is 8 (class A)

## IP Forwarding

Because prefixes are variable length, can't use old forwarding method

Need to find longest match between an IP address and the variable length prefixes
