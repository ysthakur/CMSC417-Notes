## Sub-Pieces

[BitTorrent](BitTorrent/BitTorrent.md) breaks pieces down further into sub-pieces
- Each sub-piece is about 16KB
- This is done so that we're always sending data
	- Otherwise, TCP congestion window might decrease (==TODO why? confirm==)
- The protocol always has some number of requests (~5) for a sub-piece pipelined
	- When a new sub-piece is downloaded, client sends new request
	- Helps speed things up

## Policies

### Strict Policy

Once a client requests a sub-piece of a particular piece, the sub-pieces of that same piece are requested before sub-pieces from other pieces

### Rarest First

The main policy is to pick the rarest piece first (the piece that the fewest peers have)

Benefits:
- By downloading that and re-uploading a rare piece, we make it less rare
	- If the seed dies, this increases the chances of someone having each piece
- If we have a rare piece, other peers will want to download it from us
	- When everyone downloads from us, we can download faster from them (BitTorrent's tit-for-tat algorithm)

### Random First Piece

At the start, download a random piece
- Can't start by getting a rare piece
- Downloading rare pieces is slow because we can only download their sub-pieces from a few peers

### Endgame Mode

Enter endgame mode when you're nearly done downloading and are only missing a few pieces
- These last pieces will be slower to download, because you'll have downloaded the faster-to-download, more easily accessible ones already
- Endgame mode helps avoid the last pieces becoming unobtainable
- Clients in endgame mode request last missing pieces from all of their peers (instead of just the ones they're directly connected to)
- Once a sub-piece arrives, client sends cancel message telling other peers to ignore request

---

Information taken from [How Does BitTorrent Work? A Plain English Guide](https://skerritt.blog/bit-torrent/)
