Less likely to have loops than [Distance Vector Routing](Routing/Distance%20Vector%20Routing.md) (but loops still possible)

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
	- Initially, this used time, but now it's **hop count** instead
	- Currently, IP uses 64 as default value

One link state routing protocol (implementation?) is [Open Shortest Path First (OSPF)](OSPF.md)

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
	- If get two identical copies, accept the one that came first
1. Forward LSP to all nodes except the one that sent it
2. Generate new LSP periodically; increment SEQNO
3. Start SEQNO at 0 when reboot
	- Can't maintain state to pick up at the previous SEQNO
4. Decrement TTL before flooding it to neighbors
	- Also age the stored LSP (decrement TTL)
	- Discard when TTL hits 0

## LSP processing flow

- When you get a new LSP, flood before adding to database and processing
- This is because you want to make sure the other nodes get the LSP as soon as possible
	- Processing takes time
- For shortest path routing, in practice, each switch computes its routing table directly from the LSPs it has collected using a realization of Dijkstra's algorithm called the [forward search algorithm](Forward%20search%20algorithm.md)


![LSP processing flowchart](img/link-state-routing-flowchart.png)
