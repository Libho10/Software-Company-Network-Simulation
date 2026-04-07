# Floor 2: Shared Resources & Layer 3 Switching

## Overview
Floor 2 supports mixed teams with efficient resource sharing while maintaining VLAN security. Key elements:
- **Two end-user devices per team** (DEV + BA).
- **VLAN segmentation via Layer 3 Switch** for inter-VLAN routing.
- **Shared resources**: Printer-F2, File-Server F2.
- **Single shared Router (R3-Shared)** for WAN connectivity.

This design balances collaboration (shared printer/file server) with isolation (VLANs), using L3 switching for efficient internal routing.

<img width="1784" height="609" alt="image" src="https://github.com/user-attachments/assets/f0cc1c21-0292-4d39-9c1c-1278d0fcb86b" />

*Screenshot: Floor 2 topology with L3 switch, shared resources, and R3-Shared router.*

## Device Reasoning

 Fewer devices than Floor 1 reflects shared resource focus. VLANs maintain team separation even with common infrastructure.

### VLAN Segmentation with Layer 3 Switch
- **L3 Switch**: SVIs 
- Handles inter-VLAN routing internally (no external router needed for DEV↔BA).
 L3 switching is faster than router-on-a-stick. This enables controlled access (ACLs on SVIs) between teams while sharing resources.

### Shared Resources
- **Printer-F2**: accessible by both teams.
- **File-Server F2**: shared storage/docs.

 Dedicated VLAN for infrastructure prevents resource exhaustion. Both DEV/BAs print/save files without VLAN conflicts.


### Single Shared Router (R3-Shared)
- **R3-Shared**: Default gateway for L3 switch (image will appear on Floor 3)
- Single WAN connection to ISP (no Floor 1-style redundancy needed).

Floor 2's lighter traffic justifies single router. Cost-effective while L3 switch handles internal routing efficiently.
