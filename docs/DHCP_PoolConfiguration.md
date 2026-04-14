# DHCP Pool Configuration & Team Isolation

## Overview
DHCP servers provide automated IP assignment while maintaining strict team isolation. Key features:
- **F1-Dev-DHCP**: Serves only Developer subnet with Developer_Pool.
- **F1-BA-DHCP**: Serves only Business Analyst subnet with BA_Pool.
- **Isolation through pool settings** ensures servers assign only their respective subnet gateways.
- Eliminates IP conflicts across teams through administrative separation.

<img width="805" height="834" alt="image" src="https://github.com/user-attachments/assets/310859a6-4189-483d-bbc3-5c750abf0bca" />


*Screenshot: DHCP service status on F1-Dev-DHCP and F1-BA-DHCP servers showing active pools.*

## DHCP Pool Configurations

### F1-Dev-DHCP Server (Developers_Pool)
### F1-BA-DHCP Server (BA_Pool)
