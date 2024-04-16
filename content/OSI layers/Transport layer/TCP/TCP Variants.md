[TCP](TCP.md) variants

## Tahoe (1988)

- Slow start
- Congestion avoidance
- Only does [fast retransmit](Fast%20Retransmit%20+%20Fast%20Recovery.md), no fast recovery
- Basic ideas:
	- Gently probe network for spare capacity
	- Drastically reduce rate on congestion
	- Windowing: self-clocking
	- Other functions: RTT estimation, error recovery

![Tahoe congestion window](../../../Pasted%20image%2020240415182013.png)

## Reno (1990)

- Does both [fast retransmit and **fast recovery**](Fast%20Retransmit%20+%20Fast%20Recovery.md)
- Basic ideas:
	- Fast recovery avoids slow start
	- 3 DupACKs => fast retransmit + fast recovery
	- Timeout => fast retransmit + slow start

![](../../../Pasted%20image%2020240415182028.png)

## Vegas (1994)

- Considers packet delay, not loss, as a hint for congestion
- Reno with a new congestion avoidance algorithm
- Converges! (provided buffer is large)

