# Floor 1: End-User Devices Configuration

## Floor 1 (Green)
Floor 1 hosts developer and business analyst teams with segregated networks for security, performance, and team isolation. Key elements:
- **3x F1-DEV PCs** (Developers).
- **3x F1-BA PCs** (Business Analysts).
- Dedicated switches per team.
- Independent DHCP servers per team.
- Two dedicated routers for inter-team and external routing.
- **ISP-1 and ISP-2** for dual WAN redundancy.

My design follows VLAN segmentation principles to minimize broadcast domains, enhance security, and simplify management which is ideal for a growing team environment. We also ensure high availability through ISP failover-perfect for any critical
business operations. 

<img width="626" height="884" alt="image" src="https://github.com/user-attachments/assets/880e5cc1-624d-409c-8147-650ca8b1876e" />

*Screenshot: Complete Floor 1 topology showing PCs, switches, DHCP servers, and routers.*

