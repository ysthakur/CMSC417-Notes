How many bytes the receiver can receive

Receiver calculates advertised window and sends it in [TCP Header](TCP/TCP%20Header.md)

`AdvertisedWindow = MaxRcvBuffer - ((NextByteExpected - 1) - LastByteRead)`

![Calculating advertised window](TCP/calc-advertised-window.png)

If advertised window is 0, periodically send 1 byte packets to break deadlock

Effective window (calculated at sender size) is `AdvertisedWindow - (LastByteSent - LastByteACKed)`

