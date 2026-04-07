# Floor 3: Centralized Infrastructure & Staging

## Overview
Floor 3 serves as the enterprise core with staging environments and centralized services. Key elements:
- **Staging Web Server** for pre-production demos and dev code updates.
- **Shared Router** as primary convergence for Floor 2, Floor 3, and Floor 1 routers.
- **Central Switch** with DNS, Production Web Server, and Syslog Server in dedicated subnet.
- Broadcast domain accessible from all 3 routers for unified management.

This creates a hub-and-spoke topology where Floor 3 routes inter-floor traffic while hosting critical infrastructure.

<img width="629" height="436" alt="image" src="https://github.com/user-attachments/assets/5eb8ef70-e607-42a9-a532-2513926dd17e" />

*Screenshot: Floor 3 topology showing staging server, shared router, and server farm.*

## Device Breakdown

### Staging Web Server
- **Staging Web Server**: for pre-production client demos.
- Receives code updates from Floor 1/2 developers via controlled VLAN access.
 This works because isolated staging environment prevents dev code from affecting production. Client demos happen here safely before promotion.

### Shared Router (Primary Convergence)
- **Shared Router**: Connects Floor 2 L3 Switch, Floor 3 devices, and both Floor 1 routers.
- Serves as default gateway for inter-floor routing. 

This is becuase single convergence point simplifies routing tables across floors. OSPF/EIGRP could run here for dynamic route advertisement to Floor 1 routers.


### Centralized Infrastructure (Central Switch)
- **DNS Server**: Name resolution for entire company.
- **Production Web Server**: Live customer-facing site.
- **Syslog Server**: Centralized logging from all devices.

 Dedicated infrastructure  accessible from all routers reduces management overhead. Central switch provides high-speed switching for server-to-server traffic.

<img width="695" height="342" alt="image" src="https://github.com/user-attachments/assets/d537c523-d80b-4f11-9f77-790e918e0ac8" />

*Screenshot: Centralised Infrastructure showing central switch interconnecting to DNS Server, Production Web Server and Syslog Server in dedicated subnet.*


## Traffic Flow & Inter-Floor Connectivity
1. **Floor 1 DEV → Staging Server**: F1 DEV Router → F3 Shared Router
2. **Floor 2 BA → Production DNS**: F2 L3 Switch → F3 Shared Router 
3. **All Floors → Syslog**: Device logs forwarded via central switch.
4. **Broadcast Domain**: Accessible from Floor 1 Router1, Floor 1 Router2, Floor 2, Floor 3.

There is a unified broadcast domain because infrastructure services (DNS, Syslog) need company-wide reach without complex ACL management across multiple VLANs.
