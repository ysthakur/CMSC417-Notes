- Switching based on [packets](Packet.md)
- Send out a packet into the network, have a queue of packets
- It's the network's responsibility to route all the packets to the right places
- Everyone should have a chance to send their packets
	- Can do round-robin scheduling

**Store and forward**: Entire packet must arrive at router before it can be transmitted on next link

However, introduces [delays](Delay.md) that weren't present in [circuit switching](Circuit%20switching.md)

