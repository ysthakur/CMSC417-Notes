## Routing protocols

Routing protocol goal: Determine "good" paths (routes) from sending host to receiving host, through network of routers
- "good": least cost, fastest, least congested

## Graph abstraction

- Can treat routers as graphs
	- Nodes are routers
	- Edges are links between routers
- Routing algorithms find the least cost path between two points


> [!note]
> Treating networks as graphs is also useful for [P2P](../../../PPP.md), where nodes are peers and edges are TCP connections

## Routing

For a simple network, we can calculate all shortest paths and load them into some nonvolatile storage on each node

But such a static approach has shortcomings:
- Doesn't handle node or link failures
- Doesn't consider addition of new nodes or links
- Implies edge costs cannot change

Solution: use a distributed and dynamic protocol
Two main classes of protocols:
1. [Distance Vector Routing](Distance%20Vector%20Routing.md)
2. [Link State Routing](Link%20State%20Routing.md)

### Link State Routing vs Distance Vector Routing

Link state routing is preferred for social networks

|  | LS | DV |
| ---- | ---- | ---- |
| Message complexity | With n nodes and E links, $O(nE)$ messages sent | Exchange between neighbors only |
| Speed of convergence | - $O(n^2)$ algorithm requires $O(nE)$ messages<br>- May have oscillations | - Convergence time varies<br>- May be routing loops<br>- Count-to-infinity problem |
| Robustness | - Node can advertise incorrect *link* cost<br>- Each node computes only its own table | - DV node can advertise incorrect path cost<br>- Each node's table used by others, so errors propagate through network<br> |
