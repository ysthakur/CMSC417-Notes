Hot potato routing: go for the closest egress point
- Choose local gateway that has least intra-domain cost
- Don't worry about **inter**-domain cost

This router has two [BGP](Inter-Domain%20Routing/BGP.md) routes to 192.44.78.0/24
- Hot potato: get traffic off of your network as soon as possible
- So, go for egress 1 (distance 15 < distance 56)
![](Pasted%20image%2020240503182419.png)

However, you can get "burned" by the hot potato:
- Don't want to use the link on the right
	- Even though less intra-domain distance for provider, more intra-domain distance for customer
- Solution: [Cold Potato Routing with MEDs](Cold%20Potato%20Routing.md)
![](Pasted%20image%2020240503192836.png)