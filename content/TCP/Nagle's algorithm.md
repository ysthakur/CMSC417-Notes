Sender-side solution to [Silly window syndrome](TCP/Silly%20window%20syndrome.md)

```
if there is new data to send:
  if the window size >= MSS and available data is >= MSS:
    send complete MSS segment now
  else if there is unconfirmed data still in the pipe:
    enqueue datain the buffer until an acknowledgment is received
  else: (no packets in flight, all ACKs are received)
    send data immediately, no matter how small the packet is
```
