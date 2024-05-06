---
aliases:
  - BGP Misconfiguration
---
> [!note]
> These attacks aren't actual attacks people did with malicious intent, they're just caused by misconfiguring [BGP](Inter-Domain%20Routing/BGP.md).

## Prefix Hijacking

When you originate someone else's prefix

Example: In 2010, China Telecom accidentally hijacked 15% of the Internet's prefixes

![](Inter-Domain%20Routing/prefix-hijacking.png)

### Sub-Prefix Hijacking

When you originate a more specific prefix than the real one
- For example, say an AS has a prefix 12.34.0.0/16, and you originate 12.34.158.0/24
- Every AS picks your bogus route for that prefix because traffic follows the longest matching prefix (yours)

#### Case study: Pakistan Telecom

In 2008, Pakistan Telecom wanted to block access to YouTube for its own customers
- Intended to collect and drop packets going to 208.65.153.238, 208.65.153.253, and 208.65.153.251
- But instead, they announced that Pakistan Telecom was 208.65.153.0/24
- YouTube's actual IP was 208.65.152.0/22
- So all of the Internet directed its traffic to Pakistan Telecom

How it was fixed:
- YouTube also announced that it was 208.65.153.0/24 so that some of the Internet would come to it
- YouTube then announced that it had the more specific IPs 208.65.153.128/25 and 208.65.153.0/25
- To help, Pakistan Telecom prepended its own ASN to the AS Path
	- ==TODO how does it help? google==

### Bogus AS Paths to Hide Hijacking

- Can evade detection for a bogus route by adding the legitimate AS to the end
- For example, say AS 88 wants to hijack traffic going to AS 3
	- It can AS Path `701 88` into `701 88 3` to make others think it's going to 3
- Hard to tell that the AS Path is bogus even if other ASes filter based on prefix ownership

## Path-Shortening Attacks

- Remove ASes from the AS Path
	- e.g. turn `701 3715 88` into `701 88`
- Motivations:
	- Make the AS Path look shorter than it is
	- Attract sources that normally try to avoid AS 3715
	- Help AS 88 look like it is closer to the Internet's core
- Can't tell that the AS Path is a lie
	- For all anyone knows, maybe AS 88 really does connect directly to AS 701

## Bogus AS Hop

- Add ASes to path
	- e.g. AS 701 could turn `701 88` into `701 3715 88`
- Motivations:
	- Trigger loop detection in AS 3715
		- **Denial-of-service** attack on AS 3715
		- Or blocks unwanted traffic coming from AS 3715
	- Make your AS look like it has richer connectivity
- Who can tell that the AS Path is a lie?
	- AS 3715 could, if it could see the route
	- AS 88 could, but it wouldn't care as long as it received data traffic meant for it

## Violating Consistent Export to Peers

Peers require consistent export
- Prefix advertised at all peering points
- Prefix advertised with same AS Path length

Reasons for violating this policy:
- Trick neighbor into ["cold potato"](Inter-Domain%20Routing/Cold%20Potato%20Routing.md)
	- ==TODO figure out what tricking a neighbor into cold potato means, and why you'd want that==
- Configuration mistake

Main defense: Analyzing BGP updates or data traffic for signs of inconsistency

## Other Attacks

- Attacks on BGP sessions
	- Confidentiality of BGP messages
	- Denial-of-service on BGP session
	- Inserting, deleting, modifying, or replaying messages
- Resource exhaustion attacks
	- Too many IP prefixes (e.g. BGP [512K Day](https://en.wikipedia.org/wiki/Border_Gateway_Protocol#512k_day))
	- Too many BGP update messages
- Data-plane attacks
	- Announce one BGP route, but use another

## Solutions

- Protective filtering: Know your neighbors
- Anomaly detection: Suspect the unexpected
- Checking against registries: Establish ground truth for prefix origination
- Signing and verifying: Prevent bogus AS Paths
- Data-plane verification: Ensure the path is actually followed
