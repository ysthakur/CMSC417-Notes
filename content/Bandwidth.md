## Why is it called Bandwidth?

- Bits transmitted at a particular bandwidth can be seen as having some width
- One bit transmitted at 1 Mbps can be seen as being 1 microsecond wide

## Delay and Bandwidth

- Can think of the channel between a pair of processes as a hollow pipe
	- Latency ([delay](Delay.md)) is length of the pipe
	- Bandwidth is the width of the pipe
- Scenario:
	- Delay of 50 ms
	- Bandwidth of 45 Mbps
	- $(50 \times 10^{-3} \mathrm{s}) \cdot (45 \times 10^6 \mathrm{b/s}) = 2.25 \times 10^6 \mathrm{bits} = 280 \mathrm{KB}$
- Relative importance of bandwidth and latency depends on application
	- For large file transfer, bandwidth is crucial
	- For small messages (HTTP, NFS), latency is crucial
	- Variance in latency (jitter) can also affect some applications, e.g. audio/video conferencing

## Bandwidth vs Throughput

![[Bandwidth vs Throughput]]
