Reasons for losing [packets](Packet.md):
- Queue has finite capacity
- Packets arriving to full buffer must be dropped
- Lost packet may be retransmitted by previous node, by source end system, or not at all
- The receiver isn't obligated to notify you that it dropped your packets
- So if you don't receive a reply, you can assume that your packet was dropped
