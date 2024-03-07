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
	- Positive: ACK
	- Negative: NACK
- Sender retransmits
	- After *not* receiving an ACK
	- After receiving a NACK
- Timeout by sender
	- Don't wait forever without some acknowledgment

[TCP](TCP.md)
