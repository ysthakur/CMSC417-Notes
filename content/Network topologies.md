- One possible topology:
    - Point-to-point (P2P/PPP) connections
        - Every computer is connected directly to every other computer
        - Problem: Not scalable
- Solutions:
    - Star-like topology with a central node/hub
        - Problem: network becomes centralized
    - Ring topology
        - Problem: Still not scalable with billions of computers
	- Bus topology:
		- Problem: Maximum length of link is limited
    - Multiple access
        - Shared channel, not totally centralized
        - This is what the [[Internet]] uses
        - To make sure every computer gets its chance to use the network, uses [[OSI layers/Link Layer/Switches]]
        - ![Multiple access](img/multiple_access.png)