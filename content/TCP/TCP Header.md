[TCP](TCP/TCP.md) Header

![TCP Header](TCP/tcp-header.png)

## Fields

- [Advertised window](TCP/Advertised%20window.md) - Max number of bytes receive can receive

## Flags

- PSH (push):
	- Used for chat servers
	- Send data packet immediately even if it's only a small piece of data
- URG (urgent):
	- Urgent pointer tells the receiver that the data there is important
	- Used in TELNET but not used much outside of that
