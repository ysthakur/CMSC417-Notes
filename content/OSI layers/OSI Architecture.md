---
tags:
  - osi-layer
---
- [Internet](../Internet.md) has multiple [protocol](Protocol.md) layers
- Each layer implements a service, relying on services provided by layers below
- Enables encapsulation

Example of layered network system:
1. Application programs ([Application Layer](OSI%20layers/Application%20Layer.md))
2. Process-to-process channels ([Transport Layer](OSI%20layers/Transport%20Layer.md))
3. Host-to-host connectivity ([Network Layer](OSI%20layers/Network%20Layer/Network%20Layer.md) and [Link Layer](OSI%20layers/Link%20Layer/Link%20Layer.md) (?))
4. Hardware ([Physical Layer](OSI%20layers/Physical%20Layer.md))

![Internet architecture](../img/internet-architecture.png)

## [Internet](Internet.md) protocol stack (OSI 7-layer model)

- The bottom 3 layers are implemented on all nodes
	- Network, data link, physical
- The top layers typically run only on end-to-end hosts rather than intermediate switches and routers
	- Application, presentation, session, transport

### Application layer

![Application Layer](OSI%20layers/Application%20Layer.md)

### Presentation layer

![Presentation Layer](OSI%20layers/Presentation%20Layer.md)

### Session layer

![Session Layer](OSI%20layers/Session%20Layer.md)

### Transport layer

![Transport Layer](OSI%20layers/Transport%20Layer.md)

### Network layer

![Network Layer](OSI%20layers/Network%20Layer/Network%20Layer.md)

### Link layer

![Link Layer](OSI%20layers/Link%20Layer/Link%20Layer.md)

### Physical layer

![Physical Layer](OSI%20layers/Physical%20Layer.md)
