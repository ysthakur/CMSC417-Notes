
[IP](Protocols/IP/IP.md) Addresses (IPv4):
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
- Easy to add new hosts
	- No need to update the routers
	- Doesn't require adding a new forwarding-table entry

### Class-full addressing

Global addresses:
- Properties:
	- Globally unique
	- Hierarchical: network + host
	- 4 billion [IP](Protocols/IP/IP.md) addresses, half are A type, 1/4 are B type, 1/8 are C type

![Global address format](img/global-address-format.png)

### Classful Addressing

In the olden days, only fixed allocation sizes:
1. Class A: 0*
	- Very large /8 blocks
	- There can be 126 different class A networks
2. Class B: 10*
	- Large /16 blocks
3. Class C: 110*
	- Small /24 blocks
	- $2^{21}$ different networks possible, 254 hosts
4. Class D: 1110* - for multicast groups
5. Class E: 11110* - for future use

This is why people use dotted-quad notation
