Sender-side solution to [Silly window syndrome](Silly%20window%20syndrome.md)

## Algorithm

If there is new data to send:
- If the receiver window size >= [MSS](MSS.md) and available data is >= MSS:
	- Send complete MSS segment now
- Else, if there is unconfirmed data still in the pipe:
	- Enqueue data in the buffer until an acknowledgment is received
- Otherwise: (no packets in flight, all ACKs are received)
	- Send data immediately, no matter how small the packet is
