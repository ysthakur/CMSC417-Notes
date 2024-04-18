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
