Strategy:
- Send to all nodes (not just neighbors) information about neighbors (not connection to all nodes)
- All nodes will know the link-state information of all other nodes

Link State Packet (LSP) contains:
1. The ID of the node that created the LSP
2. Costs of links to each directly connected neighbor
3. A sequence number (SEQNO)
	- Necessary because node would send out multiple packets, you need to know which one is the latest
4. A Time-To-Live (TTL) for this packet
	- To make sure old information is eventually removed from the network
	- Can use hops rather than time

## Reliable flooding

Reliable flooding: Makes sure all nodes in the network get a copy of LSP from all other nodes
- After reliable flooding, each node has a snapshot of whole network
- Now each node can calculate shortest route itself
- Can use Dijkstra's shortest path algorithm

Goals:
1. Ensure all nodes get LSPs from all others
2. Flood in minimum time
3. Minimize total routing traffic

## Algorithm

1. Store most recent LSP from each node
	- Knows which one is most recent based on sequence number
2. Forward LSP to all nodes except the one that sent it
3. Generate new LSP periodically; increment SEQNO
4. Start SEQNO at 0 when reboot
	- Can't maintain state to pick up at the previous SEQNO