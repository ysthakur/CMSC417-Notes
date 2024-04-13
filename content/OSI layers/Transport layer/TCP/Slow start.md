- A new [TCP](TCP.md) flow should start with a small [congestion window](TCP%20Congestion.md#congestion-window) (slow start) to avoid overloading network
- Initial congestion window is 1 MSS
	- So, initial sending rate is MSS/RTT
- Could be pretty wasteful:
	- Might be significantly less than actual bandwidth
	- Linear increase takes long time to get to actual bandwidth
- Slow-start phase (really "fast start")
	- Sender starts at a slow rate, but increases rate **exponentially** until first loss (double)

SSTHRES = Slow-start threshold
