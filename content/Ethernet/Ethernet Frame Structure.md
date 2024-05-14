Structure of an [Ethernet](Ethernet/Ethernet.md) frame
- Sending adapter encapsulates packet in frame
- Preamble: synchronization
	- 7 bytes with pattern `10101010`, followed by 1 byte with pattern `10101011`
	- Used to synchronize receiver, sender, clock rates
- Addresses: source and destination MAC addresses
	- Adapter passes frame to network-level protocol if destination is local MAC address or broadcast address
	- Otherwise, adapter discards frame
- Type: indicates higher level protocol
	- Usually [IP](IP/IP.md), but also others
- CRC: cyclic redundancy check

![Ethernet frame structure](Ethernet/ethernet-frame-structure.png)
