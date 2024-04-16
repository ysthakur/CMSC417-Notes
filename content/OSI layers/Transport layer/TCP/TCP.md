---
tags:
  - protocol
---
Transmission Control Protocol (TCP) is a [transport layer](../Transport%20layer.md) protocol

Maintains illusion that both hosts are using the same buffer
- Host A writes to its segment, Host B reads from its segment
- Segment sent when one of the following are true:
	- Segment full (dynamic parameter called Max Segment Size)
	- Timeout
	- "Pushed" by application

Sequence number:
- Sequence number is not necessarily globally unique, but unique to one flow
- ISN = initial sequence number
	- Chosen randomly
	- ==TODO read up on this==
- Sequence number = ISN + (number of first byte of segment)

![Maximum Segment Size](MSS.md)

## Handshakes

See [TCP Handshake](TCP%20Handshake.md)

## Header

See [TCP Header](TCP%20Header.md)

## ISN

Why does ISN have to be random?
- To prevent sequence number spoofing?
- ==TODO==

## What if SYN Packet Gets Lost?

Suppose SYN packet gets lost
- Packet lost inside network or server rejects packet (e.g. listen queue full)
- Eventually, no SYN ACK arrives
- Sender sets a timer and waits for SYN ACK
- Retransmits SYN if needed

## Tearing Down Connection

Closing each end of the connection:
1. One host calls `close()`
	- TCP sends all remaining bytes
	- TCP sends FIN to close and receive remaining bytes
2. The other host eventually gets EOF
	- Sends FIN ACK to acknowledge
3. Reset (RST) to close and not receive remaining bytes

## Calculating TCP timeout

Estimate round-trip time (RTT): $\text{EstimatedRTT} = \alpha \cdot \text{EstimatedRTT} + (1 - \alpha) \cdot \text{SampleRTT}$

$\text{Timeout} = 2 \cdot \text{EstimatedRTT}$ (double to be conservative)

- RTT estimation can be wrong
- Solution: **Karn/Partridge algorithm**
	1. Stop taking RTT samples when TCP retransmits
	2. Start again after a regular transmission/reception
	3. Each time TCP retransmits, set next timeout to be twice the last timeout value
- Problem with Karn/Partridge with rules #1 and #2
	- ??? ==TODO google==
