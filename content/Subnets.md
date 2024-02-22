- Subnets visible only within site, not visible from rest of internet
- Can put multiple subnets on one physical network
- **Subnet masks**: Apply bitwise and to get network number and subnet ID (host ID discarded)
	- Not necessary for 1s in mask to be contiguous

![Subnet masks](img/subnet-mask.png)

Forwarding algorithm:
```python
D = destination IP address
for (SubnetNum, SubnetMask, NextHop) in entries:
  D1 = SubnetMask & D
  if D1 == SubnetNum:
    if NextHop is an interface:
      deliver datagram directly to destination
    else:
      deliver datagram to NextHop (a router)
```

Uses a default router if nothing matches
