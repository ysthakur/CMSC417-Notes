---
aliases:
  - Fast Retransmit/Fast Recovery
  - FR/FR
  - Fast Retransmit
  - Fast Recovery
---
- Fast retransmit: When 3 duplicate ACKs received, retransmit the packet presumed lost without waiting for timeout
- Fast recovery (implemented in [TCP Reno](TCP/TCP%20Variants.md#Reno)): When TCP fast retransmits, instead of going into [Slow start](TCP/Congestion/Slow%20start.md) (CWND=1) like you would if it timed out, goes directly to [congestion avoidance](Congestion%20Avoidance) phase (halves CWND)

TCP Tahoe only has fast retransmit, Reno also has fast recovery

- Motivation: Prevent "pipe" from emptying after fast retransmit
- Idea: each DUP ACK represents a packet having left the pipe (successfully)
