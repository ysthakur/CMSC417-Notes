---
aliases:
  - Bencoding
---
Used by [BitTorrent](BitTorrent.md) to encode loosely structured data
- Every value has only one possible bencoding

## Supported types

4 data types supported:
- Integers
- Byte strings
- Lists
- Dictionaries

List and dictionaries may contain other lists and dictionaries, no restrictions

## Format

Uses ASCII characters as delimiters and digits
- Integers are encoded as `i<base 10 ASCII>e`
	- Leading zeroes not allowed
	- Negative values have a `-` at the start
- Byte strings are encoded as `<length>:<content>`
	- Length encoded in base 10, must be non-negative
	- Does not handle non-ASCII characters
- Lists are encoded as `l<contents>e`
	- `<contents>` is all the items in the list, bencoded, concatenated without a separator
- Dictionaries are encoded as `d<contents>e`
	- Like lists, contents are encoded as `<key1><value1><key2><value2>`, without a separator
