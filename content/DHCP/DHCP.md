---
tags:
  - protocol
aliases:
  - Dynamic Host Configuration Protocol
---
DHCP (Dynamic Host Configuration Protocol) lets you dynamically get an address from a server
- Uses [UDP](UDP)
- Only hold address while connected/on
	- Allows reuse of address
	- Can renew lease on address in use
- Support for mobile users who want to join network

In addition to [IP Address](IP/IP%20Addresses.md), also returns:
- Address of first-hop router for client
- Name and IP address of [DNS](DNS/DNS.md) server
- Network mask (to indicate network vs host portion of address)

Steps:
1. Client sends DHCP discover packet
2. DHCP server sends DHCP offer
3. Client sends DHCP request
4. DHCP server sends DHCP ACK

All of these steps are done on broadcast address so that all computers on network know about the new kid
 ![DHCP](../../img/dhcp.png)

- DHCP server maintains pool of available addresses
- There is at least one DHCP server for an administrative domain (a server or relay agent per subnet)

![DHCP Relay](DHCP%20Relay.md)

## DHCP Lease

**DHCP lease time**: the amount of time the IP address is granted to a device
- Must be renewed before lease time expires
- Or ask for new IP address after lease time expires
