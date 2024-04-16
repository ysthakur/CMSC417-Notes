- Sender sends a bunch of packets at once without waiting for ACKs right then
- Receiver sends an ACK for each packet it receives
- When the sender receives an ACK, it knows the packet was delivered, so it slides the window forward
- If a packet in the middle of the window is ACKed but not the ones before it, the end of the window moves forward but not the start
	- Window size doesn't actually grow

==TODO read more about this==

### Dealing with packet loss

1. ARQ strategy 1: Retransmit all un-ACK-ed packets
2. ARQ strategy 2: Selective retransmit
	- Retransmit only the lost packet

### TCP Cumulative ACK strategy (receiver side)

Cumulative ACK:
- Acknowledge the largest in-sequence packet received

### Implementation

- Allow a larger amount of data "in flight" for better channel utilization
- But should not exceed receiver's capacity - must all fit in buffer

Receiver buffering: flow control
- Receive window size
	- Amount that can be sent without acknowledgment
- Receiver tells the sender the window
	- Tells the sender the amount of free space left
	- Use window size field in TCP header
	- This can be sent during the three-way handshake
	- If AdvertisedWindow is 0, then:
		- Sender periodically sends 1 byte packets to break the deadlock
	- If AdvertisedWindow > Maximum Segment Size (MSS), then sender sends multiple packets
	- If AdvertisedWindow < Maximum Segment Size (MSS), then sender can make packets of size up to AdvertisedWindow

For sender:
- Effective window = Advertised window - (LastByteSent - LastByteACKed)
