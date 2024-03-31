- Process-to-process data channel
- e.g. [TCP](../TCP/TCP.md), [UDP](UDP)
- Unit of data exchanged in this layer is called a **message**

The [Session layer](Session%20layer.md) and [Presentation layer](Presentation%20layer.md) can be considered part of this layer

Two perspectives:
1. Abstraction of clients
	- Creates abstraction that intricate networks between clients doesn't exist
2. Abstraction of services
	- Provides network layer services

## Abstraction of Clients

Transport layer abstraction:
- First time admitting that data is consumed by processes, not networks

Transport protocols:
- Logical communication between processes
	- Sender divides a message into segments
	- Receiver reassembles segments into message
- Transport services
	- Multiplexing/demultiplexing packets (port numbers)
	- Detecting corrupted data (checksums)
	- Optionally: reliable delivery, flow control

### Multiplexing/demultiplexing

- Demultiplexing at recv host: delivers received segments to correct socket
- Multiplexing at send host: uses data header to indicate which socket to send to
	- Allows multiple sockets to use same data channel

Also known as mux/demux

#### Connectionless mux/demux ([UDP](UDP))

- Create sockets with port numbers
- UDP socket identified by 2-tuple `(dest IP addr, dest port number)`
- When host receives UDP segment:
	- Checks destination port number in segment
	- Directs UDP segment to socket with that port number

> [!note]
> IP datagrams with different source IP addresses and/or source port numbers are still directed to the same socket

#### Connection-orented mux/demux ([TCP](../TCP/TCP.md))

- TCP socket identified by 4-tuple
	- Source IP address
	- Source port number
	- Destination IP address
	- Destination port number
- recv host uses all four values to direct segments to appropriate socket
- Server host may support many simultaneous TCP sockets
	- Each socket identified by its own 4-tuple
- Web servers have different sockets for each connecting client
	- Non-persistent HTTP will have different socket for each request

Use case: Threaded web server

## Abstraction of Services

IP protocol stack: key abstractions
- Application layer: Applications
- Transport layer: Streams of data and messages
- Network layer: Best-effort global packet delivery
- Link layer: Best-effort local packet delivery

So transport layer is where we need to go from **best-effort** to **reliable**

Expectations for end-to-end protocols (UDP doesn't do all of these, TCP does):
- Guarantees message delivery
- Delivers messages in same order they were sent
- Delivers at most one copy of each message
- Supports arbitrarily large messages
- Supports synchronization between sender and receiver
- Allows receiver to apply flow control to sender
- Supports multiple application processes (mux/demux)

Typical limitations of the network on which the transport protocol will operate:
- Drop messages (packet loss)
- Reorder messages (out-of-order delivery)
- Deliver duplicate copies of messages
- Limit messages to some finite size
- Deliver messages after an arbitrarily long delay
- ➕ Non-zero probability of packet delivery

A reliable protocol is one that does one or more of the following:
- Guarantees message delivery
- Delivers messages in same order they were sent
- Delivers at most one copy of each message
