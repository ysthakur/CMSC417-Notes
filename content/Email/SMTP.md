---
aliases:
  - Simple Mail Transfer Protocol (SMTP)
tags:
  - protocol
---
Simple Mail Transfer Protocol (SMTP):
- Uses [TCP](TCP/TCP.md) to reliably transfer email messages from client to server
- Uses TCP port 25
- Direct transfer: Sending server (client) to receiving server (server)
- Three phases of transfer
	- Handshaking (greeting)
	- Transfer of messages
	- Closure
- Command/response interaction (like [HTTP](HTTP/HTTP.md))
	- Commands: ASCII text
	- Response: status code and phrase
- Messages must be in 7-bit ASCII
- Uses persistent connections
- Uses `<CRLF>.<CRLF>` to determine end of message (note the `.`)

Comparison with [HTTP](HTTP/HTTP.md):
- HTTP is a pull protocol, SMTP is a push protocol
- Both have ASCII command/response interaction and status codes
- In HTTP, each object is encapsulated in its own response message
- But in SMTP, multiple objects are sent in multipart messages

## Example

1. Alice uses user agent to compose message to `bob@umd.edu`
2. Alice's user agent sends message to her mail server, where it is placed in the message queue
3. Client side of SMTP opens [TCP](TCP/TCP.md) connection with Bob's mail server
4. SMTP client sends Alice's message over the TCP connection
5. Bob's mail server places the message in Bob's mailbox
6. Bob uses his user agent to read the message

Sample SMTP interaction:
```
 S: 220 hamburger.edu
 C: HELO crepes.fr
 S: 250  Hello crepes.fr, pleased to meet you
 C: MAIL FROM: <alice@crepes.fr>
 S: 250 alice@crepes.fr... Sender ok
 C: RCPT TO: <bob@hamburger.edu>
 S: 250 bob@hamburger.edu ... Recipient ok
 C: DATA
 S: 354 Enter mail, end with "." on a line by itself
 C: Do you like ketchup?
 C: How about pickles?
 C: .
 S: 250 Message accepted for delivery
 C: QUIT
 S: 221 hamburger.edu closing connection
```

