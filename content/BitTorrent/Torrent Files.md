---
aliases:
  - .torrent Files
  - Metainfo Files
---
Torrent files (aka metainfo files) contain a list of trackers and metadata for the file to download
- Use `.torrent` file extension
- Acts like a table of contents

## Schema

- `announce` - URL of the tracker
- `info` - A dictionary with the following keys:
	- `files`: A list of dictionaries, with each dictionary corresponding to a file
		- Only exists when multiple files are being shared
		- Each of these dictionaries has 2 keys:
			- `length` - Size of the file in bytes
			- `path` - A list of strings (the components of the file path)
	- `length` - Size of the file in bytes
		- Only when one file is being shared
	- `name` - Suggested file name or directory name
	- `piece length` - Number of bytes per piece
		- Must be a power of 2
		- Must be at least 16KiB
	- `pieces` - A list of the hashes for every piece of the data
		- If the torrent contains multiple files, pieces formed by concatenating all files in the order they appear in the directory
		- The last piece may be shorter than the full piece length
		- BitTorrent uses SHA-1, which returns a 160-bit hash

---

Information taken from [How Does BitTorrent Work? A Plain English Guide](https://skerritt.blog/bit-torrent/)
