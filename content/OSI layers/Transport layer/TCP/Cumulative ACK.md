A [TCP](TCP.md) receiver-side strategy.

- Acknowledge the largest in-sequence packet received
- An acknowledgment of X means that all packets up to, but not including, X, have been received
- Numbering allows detecting duplicates
- e.g. if you receive packets 5, 7, 8, 6, the ACK sequence would be 6, 6, 6, 9
