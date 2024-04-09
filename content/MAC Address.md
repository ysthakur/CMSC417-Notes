- 48-bit flat address that is locally unique
- Used locally to get frame from one interface to another physically-connected interface (inside the same network)
- Used at link layer level
- Manufacturer buys portion of MAC address space to assure uniqueness
- Burned in NIC ROM, sometimes can be set in software

## MAC Addresses vs IP Addresses

[IP Addresses](IP/IP%20Addresses.md) are used for communicating between networks, MAC addresses are used for communicating between machines within same network

Analogy:
- MAC addresses are like SSNs (shows identity, unique), whereas IP address are like postal addresses (can be changed)

MAC addresses' flat nature provides portability
- Can move LAN card from one LAN to another
- IP's hierarchical address *not* portable
	- Address depends on IP subnet to which node is attached
