---
tags:
  - osi-layer
---
- [Internet](../Internet.md) has multiple [protocol](Protocol.md) layers
- Each layer implements a service, relying on services provided by layers below
- Enables encapsulation

Example of layered network system:
1. Application programs ([Application Layer](OSI%20layers/Application%20layer.md))
2. Process-to-process channels ([Transport Layer](OSI%20layers/Transport%20layer.md))
3. Host-to-host connectivity ([Network Layer](OSI%20layers/Network%20layer/Network%20layer.md) and [Link Layer](OSI%20layers/Link%20layer/Link%20layer.md) (?))
4. Hardware ([Physical Layer](OSI%20layers/Physical%20layer.md))

![Internet architecture](../img/internet-architecture.png)

## [Internet](Internet.md) protocol stack (OSI 7-layer model)

- The bottom 3 layers are implemented on all nodes
	- Network, data link, physical
- The top layers typically run only on end-to-end hosts rather than intermediate switches and routers
	- Application, presentation, session, transport

### Application layer

![[Application layer]]

### Presentation layer

![[Presentation layer]]

### Session layer

![[Session layer]]

### Transport layer

![[OSI layers/Transport layer]]

### Network layer

![[Network layer]]

### Link layer

![[Link layer]]

### Physical layer

![[OSI layers/Physical layer]]
