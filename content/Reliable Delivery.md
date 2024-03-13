
What [TCP](TCP.md) does

Challenges of reliable data transfer:
- Over a channel with bit errors:
	- Receiver detects errors and requests transmission
- Over a lossy channel with bit errors
	- Some data are missing, others corrupted
	- Receiver cannot always detect loss
- Over a channel that may reorder packets
	- Receiver cannot distinguish loss from out-of-order

Retransmission hints:
- Acknowledgments from receiver
	- Positive: ACK (uh-huh, I heard you)
	- Negative: NACK (please repeat that)
- Sender retransmits
	- After *not* receiving an ACK
	- Or after receiving a NACK
- Timeout by sender
	- Don't wait forever without some acknowledgment

- Detects bit errors with checksum
	- If receiver detects corrupt data, requests retransmission
- Detects missing data with sequence number
	- Used to detect a gap in the stream of bytes
	- And for putting data back in order
- Recover from lost data: retransmission
	- Sender retransmits lost or corrupted data
	- 2 main ways to detect lost packets

[Automatic Repeat reQuest (ARQ)](ARQ.md)
