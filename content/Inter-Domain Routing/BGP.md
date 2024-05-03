---
tags:
  - protocol
aliases:
  - Inter-AS Routing
  - Border Gateway Protocol
---
Border Gateway Protocol (BGP) is the de-facto [Inter-Domain Routing](Inter-Domain%20Routing.md)/EGP protocol

BGP provides each AS a means to:
- eBGP (exterior BGP): Obtain subnet reachability information from neighboring ASes
- iBGP (internal BGP): Propagate reachability information to all AS-internal routers
- Determine "good" routes to other networks based on reachability information and policy

Allows subnets to advertise their existence to rest of Internet

![](ebgp-ibgp.png)

BGP session:
- Two BGP routers (peers) exchange BGP messages over semi-permanent TCP connection
	- Advertising paths to different destination network prefixes (BGP is a path vector protocol)
- When AS3 gateway router 3a advertises path `AS3,X` to AS2 gateway router 2c,
	- AS3 promises to AS2 that it will forward datagrams towards X

![](Pasted%20image%2020240430144108.png)

## Path attributes and BGP routes

- Advertised prefix includes BGP attributes
	- Prefix + attributes = route
- Two important attributes:
	1. `AS-PATH`: list of ASes through which prefix advertisement has passed
	2. `NEXT-HOP`: indicates specific internal-AS router to next-hop AS
- Policy-based routing:
	- Gateway receiving route advertisement uses import policy to accept/decline path (e.g. never route through AS Y)
	- AS policy also determines whether to advertise path to other neighboring ASes

## BGP path advertisement

- AS2 router 2c receives path advertisement `AS3,X` (via eBGP) from AS3 router 3a
- Based on AS2 policy, AS2 router 2c accepts path `AS3,X` and propagates (via iBGP) to all AS2 routers
- Based on AS2 policy, AS2 router 2a advertises (via eBGP) path `AS2,AS3,X` to AS1 router 1c

![](Pasted%20image%2020240430150634.png)

==TODO take notes on BGP path advertisement (see lecture 24)==

## BGP, OSPF, forwarding table entries

How does router set forwarding table entry to distant prefix?

==TODO take notes (see start of lecture 25)==

## BGP Route Selection

Router may learn about more than one route to destination AS, selects route based on:
1. Local preference value attribute: Policy decision
2. Shortest `AS_PATH`
3. Closest `NEXT_HOP` router: [Hot Potato Routing](Hot%20Potato%20Routing.md)
4. ...additional criteria

## Nontransit vs Transit ASes

- Internet service providers often have transit networks
- Nontransit AS might be a corporate or campus network
	- Could be a content provider

Traffic **never** flows from an ISP (transit network) through a nontransit AS to another ISP (also a transit network)

### Selective Transit

Most transit networks transit in a selective manner

![](../Pasted%20image%2020240502140801.png)

### Customers and Providers

==TODO see slide==

Customers don't always need BGP ==todo==

Customer-Provider Hierarchy ==todo==

The Peering Relationship ==todo==

Peering provides shortcuts ==todo==

## BGP Operations Simplified

1. Establish BGP session on TCP port 179
2. Exchange all active routes
3. While connection is alive, exchange incremental route update messages

## Four Types of BGP Messages

1. Open: Establish a peering session
2. Keep alive: Handshake at regular intervals
3. Notification: Shuts down a peering session
4. Update: Announcing new routes or withdrawing previously announced routes
Announcement = Prefix + Attribute values

## BGP Attributes

Most important attributes:
- `AS_PATH`
- `NEXT_HOP`
- `MULTI_EXIT_DISC`
- `LOCAL_PREF`
- ==todo more==

Attributes are used to select best routes
- Given multiple routes to the same prefix, a BGP speaker must pick at most **one** best route
	- It could reject them all

Next Hop attribute: Every time a route announcement crosses an AS boundary, the Next Hop attribute is changed to the IP address of the border router that announced the route

==TODO FINISH TAKING NOTES ON 5/2 SLIDES (LEC 25)==

