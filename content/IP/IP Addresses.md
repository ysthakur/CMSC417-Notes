---
aliases:
  - IP Address
---

[IP](IP/IP.md) Addresses (IPv4):
- A unique 32-bit number
- Identifies an interface
- Represented in dotted-quad notation

Grouping related hosts:
- The Internet is an "inter-network"
	- Used to connect networks together, not hosts
	- Need to address a network (i.e., group of hosts)

Scalability Challenge:
- Suppose hosts had arbitrary addresses
	- Then every router would need a lot of info to know how to direct packets toward every host

Hierarchical addressing (IP prefixes):
- Hierarchy is key to scalability - easy to add new hosts
	- No need to update the routers
	- Doesn't require adding a new forwarding-table entry
- Address allocated in contiguous chunks (prefixes)
- Today, the Internet has about 400,000 prefixes

## Classful Addressing

![Classful Addressing](IP/Classful%20Addressing.md)
