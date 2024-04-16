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
		- PAWS: Protect Against Wrapped Sequence Numbers (RFC 1323) - Use sequence number and timestamps
- Duplicate packets
	- Receiver maintains the last **in-sequence** byte number, say in a variable `rcv_seqno`
		- In-sequence means it's contiguous
	- If the receiver receives a packet with seq no. less than or equal to `rcv_seqno`:
		- It sends an ACK for that packet and discards the packet
	- If the receiver receives a packet with seq no. `rcv_seqno + 1`:
		- It sends an ACK for that packet and includes it in application buffer
	- If receiver receives a packet with seq no. greater than `rcv_seqno + 1`:
		- ==TODO what???==
- Timeout
	- Too short and you have wasted retransmissions
	- Too long and you have excessive delays when packet lost
	- Expect ACK to arrive after a round-trip time (RTT)
	- Set timeout as a function of the RTT
		- plus a fudge factor to account for queueing
	- Find RTT using running average of delays

## Throughput

Worked example:
- Packet size: $L = 8000$ bits
- Network bandwidth: $R = 1$ Gbps
- [Propagation delay](../Delay.md): 15 ms
- RTT: `2 * propagation_delay = 30 ms`

Transmission delay:
$$d_{\text{trans}} = \frac L R = \frac{8000}{10^9} = 8 \mathrm{\mu s}$$

Utilization (fraction of time sender busy sending):
$$U_{\text{sender}} = \frac{L/R}{RTT+L/R} = \frac{0.008}{30.008} = 0.00027$$

If you send a 1KB packet every 30.008 msec, throughput is 33 kB/sec even though the link's bandwidth is 1 Gbps
- This is pretty terrible
- Check out throughput of [Sliding Window](Sliding%20Window.md) instead
