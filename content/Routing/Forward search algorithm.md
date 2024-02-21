Used by [Link State Routing](Routing/Link%20State%20Routing.md) to compute shortest path

- Each switch maintains two lists, **Tentative** and **Confirmed**
	- Each of these lists contains a set of entries of the form (Destination, Cost, NextHop)
