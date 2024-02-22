Global addresses:
- Properties:
	- Globally unique
	- Hierarchical: network + host
	- 4 billion [IP](Protocols/IP/IP.md) addresses, half are A type, 1/4 are B type, 1/8 are C type

![Global address format](img/global-address-format.png)

In the olden days, only fixed allocation sizes:

| Class | Most significant bits | [CIDR](CIDR.md) | Address range | Notes |
| ---- | ---- | ---- | ---- | ---- |
| A | 0 | /8 | `0.0.0.0`–`127.255.255.255` | 126 different networks possible (0 and 127 reserved) |
| B | 10 | /16 | `128.0.0.0`–`191.255.255.255` | $2^{14}$ networks possible |
| C | 110 | /24 | `192.0.0.0`–`223.255.255.255` | $2^{21}$ networks possible, 254 hosts per network |
| D | 1110 | - | - | For multicast groups |
| E | 11110 | - | - | Reserved for future use |

This is why people use dotted-quad notation

## Problems with Classful Addressing

1. Wastage of addresses
2. Bigger tables to look up at routers

Enter [Classless Inter-Domain Routing (CIDR)](CIDR.md)

