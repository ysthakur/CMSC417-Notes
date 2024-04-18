---
tags:
  - protocol
---
Chord is a peer-to-peer lookup protocol that enables mapping a key/identifier to a node in the network
- It's a kind of [Distributed Hash Table](Distributed%20Hash%20Table.md)
- Fully decentralized - no node is more important than any other
- Uses [Consistent Hashing](Consistent%20Hashing.md)

The paper that introduced it: http://www.cs.berkeley.edu/~istoica/papers/2003/chord-ton.pdf

Each node has
- Node IP + key mapping
- A successor node
- Routing information about $O(\log(N))$ other nodes

## Finger Table

Chord uses a **finger table** to make key lookups faster than plain sequential queries:
- Each node $n$ maintains a routing table with up to $m$ entries, where $m$ is the number of bits in the identifier
- The $i$th entry in the table at node $n$ contains the identifier of the first node $s$ that succeeds $n$ by at least $2^{i-1}$ on the identifier circle
	- i.e., $s = successor(n+2^{i-1})$
	- where $1 \leq i \leq m$ and all arithmetic is modulo $2^m$
	- Node $s$ is called the $i$th **finger** of node $n$
- Finger table entries include Chord identifiers as well as IP address and port
