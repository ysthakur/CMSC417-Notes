Global addresses:
- Properties:
	- Globally unique
	- Hierarchical: network + host
	- 4 billion [IP Addresses](IP/IP%20Addresses.md), half are A type, 1/4 are B type, 1/8 are C type

![Global address format](img/global-address-format.png)

In the olden days, only fixed allocation sizes:

| Class | Most significant bits | [CIDR](IP/CIDR.md) | Address range                 | Notes                                                |
| ----- | --------------------- | ------------------ | ----------------------------- | ---------------------------------------------------- |
| A     | 0                     | /8                 | `0.0.0.0`–`127.255.255.255`   | 126 different networks possible (0 and 127 reserved) |
| B     | 10                    | /16                | `128.0.0.0`–`191.255.255.255` | $2^{14}$ networks possible                           |
| C     | 110                   | /24                | `192.0.0.0`–`223.255.255.255` | $2^{21}$ networks possible, 254 hosts per network    |
| D     | 1110                  | -                  | -                             | For multicast groups                                 |
| E     | 11110                 | -                  | -                             | Reserved for future use                              |

This is why people use dotted-quad notation

## Problems with Classful Addressing

- Wastage of addresses
- Bigger tables to look up at routers
	- Because there's a limited number of class A and class B networks, most people will have to use class C networks
	- But class C networks are not big enough for their purposes
	- So they'll have to get themselves multiple class C networks instead of just one network of the right size
	- Hence, more entries in routing tables

Enter [Classless Inter-Domain Routing (CIDR)](IP/CIDR.md)
