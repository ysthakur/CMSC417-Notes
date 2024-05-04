Goal: balance throughput and delay
- Huge buffers minimize drops, but add to queueing delay (thus higher RTT, longer slow start, etc.)

Queue management issues:
- Scheduling discipline
	- Which packet to send?
	- Need some notion of fairness and priority
- Drop policy
	- When should you discard a packet?
	- Which packet to discard?

## FIFO Scheduling and Drop-Tail Queueing

- Access to the bandwidth: FIFO queue
	- Packets only differentiated when they arrive
- Access to the buffer space: drop-tail queueing
	- If the queue is full, drop the incoming packet
- Drop-tail queueing leads to **bursty loss**
	- Congested link: many packets encounter full queue
	- Synchronization: many connections lose packets all at once
- Slow feedback from drop-tail:
	- Feedback comes when buffer completely full, even though the buffer has been filling for a while
	- The filling buffer is also increasing RTT, making detection even slower
	- Better to give early feedback:
		- Get 1-2 connections to slow down before it's too late

Two ways of giving early feedback:
- [Random Early Detection](TCP/Queue%20Management/RED.md) (RED)
- [Explicit Congestion Notification](TCP/Queue%20Management/ECN.md) (ECN)

## Link Scheduling

[Link Scheduling](TCP/Queue%20Management/Link%20Scheduling.md)
