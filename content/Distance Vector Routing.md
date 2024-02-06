- Each node constructs a vector containing the distances to all other nodes and distributes that vector to its immediate neighbors
- Starting assumption is that each node knows the cost of the link to each of its directly connected neighbors

![Table of costs](img/distance-vector-cost-table.png)

## Distance Vector Routing protocol

1. Advertise: A router transmits its distance vector to each of its neighbors in a routing packet
	- Two circumstances when a node sends out routing circumstances:
		1. Periodic: Automatically after some time
		2. Triggered: When an event makes a change to its routing table (e.g. link fail or new message from neighbor)
1. Each router receives and saves the most recently received distance vector from each of its neighbors
2. Update: A router recalculates its distance vector when:
	- It receives a distance vector from a neighbor containing different information than before, OR
	- It discovers that a link to a neighbor has gone down or the cost has changed

For a worked out example, see [the PowerPoint for lecture 3](https://www.cs.umd.edu/class/spring2024/cmsc417/course_materials/slides/3_internetworking_DV_routing.pptx) (specifically, slides 36 onwards)

## Distance vector algorithm

Uses [Bellman-Ford algorithm](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) (dynamic programming)

```python
def distance(x, y):
    min(distance(x, v) + distance(v, y) for v in neighbors(y))
```

Key ideas:
- From time to time, each node sends its own distance vector estimate to its neighbors
- The neighbors then update their distance vectors using Bellman-Ford
- Under minor, natural conditions, the distance estimates converge to the actual least costs

Each node `x` does the following:

1. Initialize `x`
2. For every node `y`:
	- If `y` is a neighbor, then `D[x][y] = cost(x, y)`
	- Otherwise, `D[x][y] = infinity`
3. Send distance vector `D[x]` to all neighbors
4. Loop forever:
	1. Wait until you receive a distance vector from some neighbor `w`
	2. For each node `y`, update distance to `y` using Bellman-Ford
	3. If the distance to any of the neighbors was updated, send the new distance vector to all neighbors

Algorithm characteristics:
- Iterative, asynchronous
	- Each local iteration caused by:
		- Local link cost change
		- Distance vector update message from neighbor
- Distributed
	- Each node notifies neighbors *only* when distance vector changes
		- Neighbors then notify their neighbors if necessary

## Link failure and cost updates

1. Node detects local link cost change
2. Updates routing info, recalculates distance vector
3. If distance vector changes, notify neighbors

If link fails, cost is updated to infinity

PowerPoint 3 (linked somewhere above) shows it step-by-step

### Count-to-infinity problem

==TODO take notes on this==
