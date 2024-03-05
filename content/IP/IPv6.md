[IP](IP.md)

128-bit address:
- Eight 16-bit chunks
- Last 64 bits used for host address

Differences from IPv4
- Has unicast, **anycast**, multicast addressing
	- No concept of broadcast
- No header checksum
	- Application layer protocols have their own checksums, so no need for IP to do it
- No fragmenting-related options
	- If a packet exceeds MTU, it's dropped
	- Message sent back to source saying it was dropped
	- Source host's responsibility to fragment the packet and resend
	- **MTU discovery** helps with this

## Anycast

- Suppose you're Googling something
- Want to reach nearest google.com server
- Use anycast to reach any server with the IP address for google.com
- Multiple servers can advertise the same IP address
- If a router gets advertisements from two servers with the same IP address, it will just think there's two paths to the same server and will choose the shortest path (which is actually the closer server)

## IPv4 and IPv6 Co-existence

- A router may not support IPv6
- Act like virtual network - encapsulate IPv6 packet in an IPv4 packet
