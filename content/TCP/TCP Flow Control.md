- Goal: Maximum utilization of the resources without overwhelming the receiver

## Implementation

[TCP](TCP/TCP.md) uses [Sliding Window](../../../ARQ/Sliding%20Window.md) algorithm:

- Allow a larger amount of data "in flight" for better channel utilization
- But should not exceed receiver's capacity - must all fit in buffer

## Receiver Buffering: Flow Control

- Receive window size (aka [Advertised window](TCP/Advertised%20window.md))
	- Amount that can be sent without acknowledgment
- Receiver tells the sender the window
	- Tells the sender the amount of free space left
	- Use window size field in TCP header
	- This is sent during the three-way handshake and each subsequent ACK
	- If AdvertisedWindow is 0, then:
		- Sender periodically sends 1 byte packets to break the deadlock
	- If AdvertisedWindow > Maximum Segment Size (MSS), then sender sends multiple packets
	- If AdvertisedWindow < Maximum Segment Size (MSS), then sender can make packets of size up to AdvertisedWindow

For sender:
- Effective window = Advertised window - (LastByteSent - LastByteACKed)
