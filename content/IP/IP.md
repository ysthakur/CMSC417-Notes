---
aliases:
  - Internet Protocol
tags:
  - protocol
---
- IP = Internet Protocol
- Runs on all the nodes in a collection of networks and defines the infrastructure that allows these nodes and networks to function as a single logical internetwork

![IP hourglass](../../../img/ip-hourglass.png)

## IP Service Model

- Packet delivery model
	- Connectionless - only cares about handing to right neighbor, doesn't need a connection
	- Best-effort delivery (unreliable service)
		- Packets are **lost**
		- Packets are delivered **out of order**
		- **Duplicate** copies of packet are delivered
		- Packets can be **delayed** for a long time
- Global addressing scheme
	- Provides a way to identify all hosts in the network

## IP datagram format (packet format)

- In the image below, at the bottom is the data (variable size)
	- Data size = datagram length - header length
- Everything above is the header
	- Variable size (20 bytes default without options)
- It only has a checksum for the header (not the data) because it only cares about the header
	- Higher level protocols will deal with the data

![IP datagram format](../../../img/ip-datagram-format.png)

- IP doesn't have a separate data length field, you can calculate it with packet length - header length

Header checksum:
- Tells you if there was any corruption
- Only checksum of header because up to lower layers to handle corruption of data
- Works by treating the header as 16-bit words, adding them up, and taking one's complement of that

## IP Fragmentation and Reassembly

- **Maximum Transmission Unit (MTU)** - Maximum length of packet
	- Default 1500 bytes
	- This is used because of hardware limitations
	- Larger packets occupy a link for longer
- If packet length is bigger than some router's MTU, need to fragment it
- Packets get reassembled at destination:
	- If did at router, there'd be additional computation and delay
	- Packet might fragment again during transit
	- Different fragments may take different routes, so they may not even be available at intermediate routers
- 16-bit identifier is used to reassemble them (`Ident` field)
	- Packets may have duplicate identifiers
	- To help with this, 2-minute time limit used initially
	- But this may not be enough with large networks
	- Deduplication: if router sees duplicate packets, it will discard them
- Flags (see "flgs" in the diagram above):
	- `DF` (Don't Fragment): When set to 1, drops the packet instead of fragmenting if size over MTU
		- ==TODO when is this useful?==
	- `MF` (More Fragments): When set to 1, indicates that more fragments of the packet are to come
- Fragment offset (see diagram above):
	- Identifies fragment location relative to beginning of unfragmented data
	- Fragments are counted in units of 8 octets (8-byte blocks)
	- This allows fragmenting fragments further (fragment index alone would not)
- If not all of the fragments arrive, host discards even the fragments that did arrive
	- IP does not bother recovering from missing fragments
