Mobility is a spectrum:
- No mobility: Mobile wireless user, using same [Access Point](LAN%20Architecture/Access%20Point.md)
- More mobility: Mobile user, connecting/disconnecting from network using DHCP
- High mobility: Mobile user, passing through multiple access points while maintaining ongoing connections (like cell phone)

## Vocabulary

- Home network: "home" of mobile (e.g. 128.119.40/24)
- Permanent address: address in home network, can always be used to reach mobile
	- Remains constant
	- e.g. 128.119.40.186
- Home agent: Entity that will perform mobility functions on behalf of mobile, when mobile is remote
- Visited network: Network in which mobile currently resides
	- e.g. 79.129.13/24
- Care-of-address: Address in visited network
	- e.g. 79.129.13.2
- Foreign agent: Entity in visited network that performs mobility functions on behalf of mobile
- Correspondent: Wants to communicate with mobile

## Approaches

- Let routers handle it
	- Routers advertise permanent address of mobile-nodes-in-residence via usual routing table exchange
	- Routing tables indicate where each mobile located
	- No changes to end-systems
	- **Not scalable to millions of mobiles**
- Let end-systems handle it
	- Indirect routing: Communication from correspondent to mobile goes through home agent
		- Home agent forwards to foreign agent
		- Foreign agent forwards to mobile
	- Direct routing: Correspondent gets foreign address of mobile, then sends directly to mobile

## Registration

1. Mobile contacts foreign network on entering visited network
2. Foreign agent contacts home agent home: "this mobile is resident in my network"

End result:
- Foreign agent knows about mobile
- Home agent knows location of mobile

