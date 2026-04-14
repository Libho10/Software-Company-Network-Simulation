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
# Automatic DHCP Parameter Assignment Verification

## Overview
All six Floor 1 PCs automatically receive complete network parameters from their respective DHCP servers, proving successful isolation and automation. Key verification:
- **3x F1-DEV PCs** get parameters from **F1-Dev-DHCP (Developer_Pool)**.
- **3x F1-BA PCs** get parameters from **F1-BA-DHCP (BA_Pool)**.
- **Four required parameters** auto-populated: IP Address, Subnet Mask, Default Gateway, DNS Server.

This validates both DHCP servers distribute team-specific configurations matching their router interfaces.

## DHCP Parameter Verification Table

| PC Name     | IP Address     | Subnet Mask     | Gateway         | DNS Server      | DHCP Server      |
|-------------|----------------|-----------------|-----------------|-----------------|------------------|
| **F1-DEV-1**| 192.168.0.5 | 255.255.255.224  | 192.168.0.1   | 10.10.10.13  | **F1-Dev-DHCP** |
| **F1-DEV-2**| 192.168.0.4 | 255.255.255.224  | 192.168.0.1   | 10.10.10.13  | **F1-Dev-DHCP** |
| **F1-DEV-3**| 192.168.0.3 | 255.255.255.224  | 192.168.0.1   | 10.10.10.13  | **F1-Dev-DHCP** |
| **F1-BA-PC1** | 192.168.0.36 | 255.255.255.224  | 192.168.0.33   | 10.10.10.13  | **F1-BA-DHCP**  |
| **F1-BA-PC2** | 192.168.0.35 | 255.255.255.224  | 192.168.0.33   | 10.10.10.13  | **F1-BA-DHCP**  |
| **F1-BA-PC3** | 192.168.0.37 | 255.255.255.224 | 192.168.0.33   | 10.10.10.13  | **F1-BA-DHCP**  |

## Individual PC Verification Screenshots

### F1-DEV PCs (DHCP Mode Confirmed)
<img width="496" height="793" alt="image" src="https://github.com/user-attachments/assets/4085b93c-d223-48a6-8f54-337462cd8d9c" />

*All 3 DEV PCs show "DHCP Enabled: Yes" with Developer_Pool parameters matching R1 interface (192.168.10.1).*

### F1-BA PCs (DHCP Mode Confirmed)  
<img width="496" height="794" alt="image" src="https://github.com/user-attachments/assets/7b283d26-25a4-45e9-ab02-7b78387ad88e" />

*All 3 BA PCs show "DHCP Enabled: Yes" with BA_Pool parameters matching R2 interface (192.168.20.1).*

## Key Success Criteria Met

 **Automatic Parameter Population**: All 6 PCs auto-configured without static IPs  
**Correct Subnet Isolation** 
 **Matching Gateways**: Points to team-specific routers 
 **Central DNS Reachability**: All PCs receive Floor 3 DNS (10.10.10.13)  
 **Zero Conflicts**: Clean IP distribution across 41 available addresses per pool  

**Result**: Fully automated, zero-touch provisioning for Floor 1 end-users. DHCP isolation works perfectly.
