- Process-to-process data channel
- e.g. [TCP](TCP), [UDP](UDP)
- Unit of data exchanged in this layer is called a [Message](../Message.md)

The [Session layer](Session%20layer.md) and [Presentation layer](Presentation%20layer.md) can be considered part of this layer

Two perspectives:
1. Abstraction of clients
	- Creates abstraction that intricate networks between clients doesn't exist
2. Abstraction of services
	- Provides network layer services

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

## Multiplexing/demultiplexing

- Demultiplexing at recv host: delivers received segments to correct socket
- Multiplexing at send host: uses data header to indicate which socket to send to
	- Allows multiple sockets to use same data channel