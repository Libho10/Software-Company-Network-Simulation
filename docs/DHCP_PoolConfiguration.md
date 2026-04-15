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

*All 3 DEV PCs show "DHCP Enabled: Yes"*

### F1-BA PCs (DHCP Mode Confirmed)  
<img width="496" height="794" alt="image" src="https://github.com/user-attachments/assets/7b283d26-25a4-45e9-ab02-7b78387ad88e" />

*All 3 BA PCs show "DHCP Enabled: Yes"*

## Key Success Criteria Met

 **Automatic Parameter Population**: All 6 PCs auto-configured without static IPs  
**Correct Subnet Isolation** 
 **Matching Gateways**: Points to team-specific routers 
 **Central DNS Reachability**: All PCs receive Floor 3 DNS (10.10.10.13)  
 **Zero Conflicts**: Clean IP distribution across 41 available addresses per pool  

**Result**: Fully automated, zero-touch provisioning for Floor 1 end-users. DHCP isolation works perfectly.

# Cross-Subnet Ping Tests: Traffic Isolation Proof

## Overview
Cross-subnet ping tests confirm **100% traffic isolation** between Developer and Business Analyst teams. Key results:
- **F1-DEV-PC1 → F1-BA-PC3**: 100% packet loss (192.168.0.36 unreachable).
- **F1-BA-PC1 → F1-DEV-PC1**: 100% packet loss (192.168.0.5 unreachable).
- **Proves proper subnet segmentation** between VLAN 10 (DEV) and VLAN 20 (BA).

This security requirement ensures development code cannot leak to business analysts.

## Test Results Table

| Source PC      | Destination PC | Target IP       | Pings Sent | Pings Received | **Packet Loss** | **Result**          |
|----------------|----------------|-----------------|------------|----------------|---------------|---------------------|
| **F1-DEV-PC1** | F1-BA-PC3     | **192.168.0.36** | 4        | **0**          | **100%**       |  **ISOLATED**     |
| **F1-BA-PC1**  | F1-DEV-PC1    | **192.168.0.5**  | 4        | **0**          | **100%**       |  **ISOLATED**     |

## Detailed Test Verification

### Test 1: F1-DEV-PC1 → F1-BA-PC3 (192.168.0.36)

<img width="940" height="347" alt="image" src="https://github.com/user-attachments/assets/9c94696e-5cca-409f-abb0-43ff958cfcd8" />

*Screenshot: F1-DEV-PC1 ping to F1-BA-PC3 showing 100% loss.*

### Test 2: F1-BA-PC1 → F1-DEV-PC1 (192.168.0.5)

<img width="940" height="393" alt="image" src="https://github.com/user-attachments/assets/3b0aced6-2e9a-40db-86cd-274c35e20535" />


 *Screenshot: F1-BA-PC1 ping to F1-DEV-PC1 showing 100% loss.*

**Test Conclusion**: Perfect isolation achieved. Zero unauthorized cross-team communication.
