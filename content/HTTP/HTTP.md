---
aliases:
  - Hyper-Text Transfer Protocol (HTTP)
tags:
  - protocol
---
Hyper-Text Transfer Protocol (HTTP)
- Stateless: Server maintains no information about past client requests
- Uses [TCP](TCP/TCP.md) (client connects to port 80 on the server)
- At [Application Layer](OSI%20layers/Application%20Layer.md)

Review of web stuff:
- Web pages consist of objects
- Objects can be HTML files, images, audio files, etc.
- Web page consists of base HTML file which includes several referenced objects
- Each object is addressable by a [URL](HTTP/URL.md)

Client/server model:
- Client: Browser that requests, receives, and displays web objects
- Server: Web server sends objects in response to requests

## Non-persistent and persistent HTTP

Non-persistent HTTP:
- At most one object sent over connection
- Every time it wants to request something, it opens a new connection, does the handshake, gets the thing, and then closes the connection again
- Bad if you want to download a bunch of objects

Persistent HTTP:
- Server leaves connection open after sending response
- Subsequent HTTP messages sent over open connection
- Don't need an extra handshake for every HTTP request

## Other optimizations

### Pipelining

Send several requests at once

### HTTP/2

Push resources rather than pull them
- After client's first request, server can send all relevant objects without waiting for requests

### QUIC

- Eliminates first RTT
- Client initiates QUIC connection and immediately requests file
- Server sends back file instead of shaking hands

![](HTTP/http-quic.png)

## HTTP Request Messages

- ASCII, human-readable

![](HTTP/http-request-example.png)

![](HTTP/http-request-format.png)

## Methods

HTTP/1.0:
- `GET`
- `POST`
- `HEAD`: Asks server to leave requested object out of response

HTTP/1.1 has those and:
- `PUT`: Uploads file in entity body to path specified in URL field
- `DELETE`: Deletes file specified in URL field

Two ways to upload form input:
- Send `POST` request:
	- Web page includes form input
	- Input is uploaded to server in entity body
- Send `GET` request:
	- Input is included in URL search params

## HTTP Responses

![](HTTP/http-resp-example.png)

### Status Codes

Some sample status codes:
==TODO what are the ranges?==
