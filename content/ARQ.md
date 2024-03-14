---
aliases:
  - Automatic Repeat reQuest (ARQ)
---
Automatic Repeat reQuest (ARQ)

- ACK and timeouts
	- Receiver sends ACK when it receives packet
	- Sender waits for ACK and times out
- Two variations
	- Stop and wait
		- Simplest ARQ protocol
		- Send a packet, stop and wait until ARQ arrives
		- Not used as much anymore because sliding window is better
	- Sliding window

## Stop and wait

- Each packet has a unique identifier
- Receiver sends acknowledgment (ACK) after successfully receiving a packet
	- The ACK contains the identifier of the received packet
- The sender sends packet no. `k+1` if and only if it receives ACK for packet no. `k`

Design decisions:
- Unique packet identifiers
	- The sequence number will eventually wrap around
	- With a high enough bandwidth, this can happen very quickly
	- So use wrap-around-aware sequence number comparison
		- $A < B$ if $0 < (B - A) < 2^{31}$
		- PAWS (RFC 1323)
- Duplicate packets
	- Receiver maintains the last **in-sequence** byte number, say in a variable `rcv_seqno`
		- In-sequence means it's contiguous
	- If the receiver receives a packet with seq no. less than or equal to `rcv_seqno`:
		- It sends an ACK for that packet and discards the packet
	- If the receiver receives a packet with seq no. `rcv_seqno + 1`:
		- It sends an ACK for that packet and includes it in application buffer
	- If receiver receives a packet with seq no. greater than `rcv_seqno + 1`:
		- ???
- Timeout
	- Too short and you have wasted retransmissions
	- Too long and you have excessive delays when packet lost
	- Expect ACK to arrive after a round-trip time (RTT)
	- Set timeout as a function of the RTT
	- Find RTT using running average of delays

## Sliding window

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
