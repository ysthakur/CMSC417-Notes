An unintuitive application using [ICMP](ICMP/ICMP.md)
- Works by sending packets with small TTLs
- When TTL hits 0, router will respond with ICMP Time Exceeded message
- Use these Time Exceeded messages to identify routers
- So TTL=1 will result in a message from the first router, TTL=2 will result in a message from the second router, and so on
- Keep incrementing TTL until you hit destination

Covered in lecture 11, but the slides aren't super useful
