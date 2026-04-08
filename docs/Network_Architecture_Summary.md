# Network Architecture Summary & Key Design Decisions

## Overall Topology
The three-floor design creates a **triangle topology** with Floor 3's R3-Shared router as the central convergence point:
- **R3-Shared** directly connects to **R1 (Floor 1 DEV Router)** and **R2 (Floor 1 BA Router)**.
- Floor 2 L3 Switch connects to R3-Shared for inter-floor routing.
- Forms robust hub-and-spoke architecture with Floor 3 as the core.
  
<img width="1758" height="618" alt="image" src="https://github.com/user-attachments/assets/d7fa4e60-400e-4fa6-857d-70e033654018" />

*Screenshot: Full 3-floor topology showing triangle connectivity between R1-R2-R3, Floor 2 L3 switch, and ISP redundancy.*

## Architecture Strengths

### Triangle Topology (R1 ↔ R3 ↔ R2)
Multiple paths prevent single points of failure. R3-Shared handles inter-floor routing while R1/R2 maintain Floor 1 team isolation.
### Seamless Scalability
- **Floor 1**: Dedicated routers/switches per team (scale teams independently).
- **Floor 2**: L3 switching for shared resources (add users/resources easily).
- **Floor 3**: Centralized infrastructure (add servers without re-architecting).
