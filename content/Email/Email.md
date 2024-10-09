In the [Application Layer](OSI%20layers/Application%20layer.md)

Three major components:
- User agents, a.k.a. mail readers
	- Composing, editing, reading mail messages
	- e.g. Outlook, Thunderbird, iPhone mail client
	- Outgoing and incoming messages stored on server
- Mail servers
	- Mailbox containing incoming messages for user
	- Message queue of outgoing messages (messages to be sent)
	- [SMTP](Email/SMTP.md) protocol between mail servers to send email messages
		- Client: sending mail server
		- Server: receiving mail server
- [Simple Mail Transfer Protocol (SMTP)](Email/SMTP.md)

## Mail message format

SMTP: protocol for exchanging email messages

RFC 822: Standard for text message format
- Header lines (different from SMTP's `FROM`, `RCPT TO` commands!):
	- `To:`
	- `From:`
	- `Subject:`
- CLRF separating header from body
- Body: ASCII characters only

## Mail access protocols

- [SMTP](Email/SMTP.md): Delivery/storage to receiver's server
- Mail access protocol: retrieval from server
	- POP: Post Office Protocol: authorization, download
	- IMAP: Internet Mail Access Protocol: more features, including manipulation of stored messages on the server
	- HTTP: Gmail, Hotmail, Yahoo, etc.
