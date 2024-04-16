# Congestion Control with a Misbehaving Receiver

- A client can implicitly control the data rate of a remote server
	- Not an implementation error
	- Weakness in [TCP](TCP.md) spec
	- TCP's design doesn't consider that senders and receivers can have disjoint interests

## Vulnerabilities

### ACK Division

Bytes vs Segments:
- CWND limits unacknowledged data
- TCP begins a session in slow start

Exploit:
- When receive a data segment with $N$ bytes, send $M$ ACKs for one packet, where $M \leq N$
- Exponential growth factor proportional to $M$
- ✅ Preserves end-to-end semantics

Countermeasures:
- Only increase ACKs when receiver ACKs >= 1
- Byte counting

### DupACK Spoofing

[Fast Retransmit + Fast Recovery](Fast%20Retransmit%20+%20Fast%20Recovery.md):
- If receive out-of-order segment, sends DupACK
- If sender receives 3 DupACKs,
	- it fast retransmits and enters fast recovery
	- CWND = CWND / 2 + 3 \* SMSS
	- On a DupACK += SMSS

Exploit:
- Send extra duplicate ACKs to trigger fast recovery
- Sender sends one packet for each duplicate ACK
- ✅ Preserves end-to-end semantics

Countermeasures:
- Count outstanding segments
- Ignore extra DupACKs

### Optimistic ACKing

When sender receives a new ACK, it increases CWND
- But receiver might not actually have received the packet!

Exploit:
- So, receiver sends ACKs early
- Sender sends packets in proportion to ACK rate
- ❌ Violates end-to-end semantics
- ❌ Lose reliability

Countermeasures:
- Randomize segment boundaries
- Ignore ACKs unless they match a real boundary