---
aliases:
  - Switching
---
To allow multiple computers to share one point
- Essentially the same as a [bridge](Bridges.md),
- but typically used to connect individual hosts rather than LANs

One way of switching is [[Circuit switching]], which was used for telephones but doesn't work well for the [[Internet]]

Instead, [[Packet switching]] is used
 ![[switching.png]]

## Traffic Isolation

- Switch filters packets
	- Frame only forwarded to the necessary segments
	- Segments can support separate transmissions

### Self-learning: Building the Table

When a frame arrives:
- Inspect the source MAC address
- Associate the address with the incoming interface
- Store the mapping in the switch table
- Use a timer to eventually forget the mapping

### Self-learning: Handling Misses

When frame arrives with unfamiliar destination:
- Forward the frame to all the interfaces except for the ones where the frame arrived
- Hopefully, this case won't happen often

## Advantages over [Hubs/Repeaters](../Physical%20layer.md)

- Only forward frames as needed
	- Avoid unnecessary load on segments
- Wider geographic span
	- Separate segments allow longer distances
- Improves privacy
	- Hosts can "snoop" traffic traversing their segment, but not the rest of the traffic
- Can join segments that use different technologies

## Difference between switches and routers

![Switch vs Router](../../Switch%20vs%20Router.md)