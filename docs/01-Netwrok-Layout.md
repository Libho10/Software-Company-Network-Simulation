# Network Layout
## **This is what the Network layout does for the business**

| Office Problem | My Network Solution | $$ Business Value |
|----------------|------------------|-------------------|
| Teams see each other's files | Separate "digital floors" | **Data Privacy** |
| Manual computer setup | Auto-addressing (DHCP) | **Zero IT calls** |
| Client demos risk hacking | Locked "demo room" | **Safe demos** |

 ## My 3-Floor Netwrok 
 <img width="1904" height="723" alt="Screenshot 2026-02-18 190107" src="https://github.com/user-attachments/assets/f5b07a73-4c42-4b4d-9818-b75a5a968884" />

**Floor 1:** 3 Developers + 3 Analysts + 2 Routers  
**Floor 2:** 2 Testers + 2 Designers + Shared Switch  
**Floor 3:** Client Demo Server  
**Central:** DNS (192.168.0.13), Production Web, Syslog

##  **Smart Engineering Choice**
**Challenge:** Router had 3 ports, needed 4 devices  
**Solution:** **GigabitEthernet0/0 shares multiple devices**  
**Result:** **Saved money** on extra hardware

##  Files
- **Total:** 10 PCs + 3 Routers + 1 Switch + 4 Servers
