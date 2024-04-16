## Kinds of Scheduling
### FIFO Scheduling

- Simple, but restrictive
- Example showing it's: two kinds of traffic
	- VoIP needs low delay
	- Email is not that sensitive about delay
	- With FIFO scheduling, voice traffic might have to wait behind email (**not good**)

### Strict Priority

- Multiple levels of priority
	- Always transmit high-priority traffic, when present
- Isolation for the high-priority traffic
	- Almost like it has a dedicated link (except for small delay for packet transmission)
- But, lower priority traffic may starve (not good)

### Weighted Fair Scheduling

- Assign each queue a fraction of the bandwidth
- Rotate across queues on a small time scale
- Work-conserving: send extra traffic from one queue if others are idle

## Implementation Trade-Offs

- FIFO: one queue, trivial scheduler
- Strict priority: one queue per priority level, simple scheduler
- Weighted fair scheduling: one queue per class, more complex scheduler
