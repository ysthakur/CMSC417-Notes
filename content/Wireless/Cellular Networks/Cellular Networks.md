## Architecture

Cell:
- Covers geographical region
- [Base Station](Wireless/Wi-Fi/802.11%20LAN%20Architecture/Base%20Station.md) (BS): Analogous to 802.11 [AP](Wireless/Wi-Fi/802.11%20LAN%20Architecture/Access%20Point.md)
- Mobile users attach to network through BS
- Air-interface: Physical and link layer protocol between mobile and BS

Mobile Switching Center (MSC):
- Connects cells to wired telephone network
- Manages call setup
- Handles mobility

![](Wireless/Cellular%20Networks/cellular-network-architecture.png)

## The first hop

Two techniques for sharing mobile-to-BS radio spectrum (see [Multi-Access Protocol](OSI%20layers/Link%20layer/Multi-Access%20Protocol.md)):
1. Combined FDMA/TDMA: Divide spectrum into frequency channels, divide each channel into time slots
2. CDMA: Code division multiple access
