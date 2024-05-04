---
aliases:
  - BitTorrent Resource Allocation
  - Tit-for-tat
---
Choking is when you refuse to upload to a peer
- But you can still download from them
- Principle: upload to peers who have uploaded to us
	- Tit-for-tat algorithm
- We want to achieve **Pareto Efficiency**
	- An allocation is Pareto Efficient if there is no allocation in which some individual is better off without any other individual being worse off

Which peers to choke/unchoke?
- A peer always unchokes a fixed number of its peers (by default, 4)
- Which peers to unchoke based on current download rates
	- Use a 20-second average of the download rate
- Calculate which peers to choke/unchoke every 10 seconds
	- This is because rapidly choking/unchoking will make TCP go back to slow start
- Choking peers based on how much they upload prohibits "free riders"

## Optimistic Unchoking

Optimistic unchoking is when you have 1 additional unchoked peer whose download rate isn't considered
- The optimistic unchoke is shifted every 30 seconds
- The optimistic unchoke is randomly selected

Why?
- If you don't optimistically unchoke peers, then you won't ever upload to them, so they won't ever upload to you
- Optimistic unchoking also allows free riders to download some data, though very slowly

---

Information taken from [How Does BitTorrent Work? A Plain English Guide](https://skerritt.blog/bit-torrent/)
