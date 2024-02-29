---
aliases:
  - Network Address Translation
---
NAT (Network Address Translation)
- You get a private [IP address](IP%20Addresses.md) within your network
- Rest of the world only sees your router's IP address
- All datagrams leaving local network have same single source NAT IP address
- *But* different source port numbers

Works using NAT translation table:
- Each row has WAN side address and corresponding LAN side address

NAT implementations must:
- Replace outgoing datagrams
- Remember (in NAT table) every (source IP, port #) to (NAT IP, new port #) translation pair
- Replace incoming datagrams

Reasons for private addresses:
- More IP address space
- Can change addresses of devices in local network without notifying outside world
- Can change ISP without changing addresses of devices in local network
- Devices in local network can't be explicitly addressed by outside world (security)

Problems:
- Violates end-to-end argument
	- Cannot predict latency because don't know how deep network is
	- One IP address no longer means one device
		- Must be taken into account by peer-to-peer applications
- NAT traversal: what if client wants to connect to a server hidden behind NAT?
- 16-bit port-number field
	- Over 60,000 simultaneous connections with a single LAN-side address

> [!Fun fact]
> NAT is not standardized
