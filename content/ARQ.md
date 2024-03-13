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

### Stop and wait

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

### Sliding window


