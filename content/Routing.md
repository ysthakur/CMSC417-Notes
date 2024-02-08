## Routing protocols

Routing protocol goal: Determine "good" paths (routes) from sending host to receiving host, through network of routers
- "good": least cost, fastest, least congested

## Graph abstraction

- Can treat routers as graphs
	- Nodes are routers
	- Edges are links between routers
- [Routing algorithms](Routing%20algorithms) find the least cost path between two points


> [!note]
> Treating networks as graphs is also useful for [P2P](Protocols/PPP.md), where nodes are peers and edges are TCP connections

## Routing

For a simple network, we can calculate all shortest paths and load them into some nonvolatile storage on each node

But such a static approach has shortcomings:
- Doesn't handle node or link failures
- Doesn't consider addition of new nodes or links
- Implies edge costs cannot change

Solution: use a distributed and dynamic protocol
Two main classes of protocols:
1. [Distance Vector Routing](Distance%20Vector%20Routing.md)
2. [Link State Routing](Link%20State%20Routing)