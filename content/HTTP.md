---
aliases:
  - Hyper-Text Transfer Protocol (HTTP)
tags:
  - protocol
---
Hyper-Text Transfer Protocol (HTTP)

- Uses TCP

Client/server model:
- Client: Browser that requests, receives, and displays web objects
- Server: Web server sends objects in response to requests

## Non-persistent HTTP

- At most one object sent over connection
Every time it wants to request something, it opens a new connection, does the handshake, gets the thing, and then closes the connection again

## HTTP/2

Push protocol rather than pull protocol
- After client's first request, server can send all relevant objects without waiting for requests

## Cookies


