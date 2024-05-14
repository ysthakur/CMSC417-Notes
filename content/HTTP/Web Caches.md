---
aliases:
  - Proxy Servers
---
Goal: Satisfy client request without involving origin server

- User sets browser: Web accesses via cache
	- ==todo what does that mean?==
- Browser sends all [HTTP](HTTP/HTTP.md) requests to cache
	- If object is in cache, proxy server returns object
	- Otherwise, cache requests object from origin server, then forwards to client

- Cache acts as both client and server
	- Server for original requesting client
	- Client to origin server
- Cache is typically installed by ISP (university, company, residential ISP)

Motivation:
- Reduce response time for client requests
- Reduce traffic on an institution's access link
- Internet dense with caches
	- Enables "poor" content providers to effectively deliver content

![](HTTP/web-cache.png)
