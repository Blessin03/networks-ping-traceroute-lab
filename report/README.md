# Network Measurement Project: Ping and Traceroute Analysis

## Context

This project explores how basic network diagnostic tools—`ping` and `traceroute`—behave across different destinations and packet sizes.  
The goal is not just to collect output, but to separate **raw observations**, **derived analysis**, and **human-readable conclusions** in a way that mirrors real-world engineering practice.

The structure of this repository intentionally follows patterns used in:
- networking research
- SRE incident reports
- performance diagnostics
- infrastructure postmortems

---

## Methodology

Measurements were collected from a single  machine using standard ICMP-based tools.

### Tools Used
- `ping` with controlled packet sizes and fixed counts ( (1/9000)/ 20)
- `tracert` (Windows traceroute)

### Test Dimensions
- **Packet size:** 1 byte vs. 9000 bytes
- **Geographic distance:**  
  - University of Florida (regional)  
  - University of Queensland (intercontinental)  
  - University of the West Indies (regional international)

### Data Handling Rules
- Raw command output is stored  in `data/`
- No interpretation or screenshots are mixed into raw data
- All conclusions are derived exclusively from the raw files

---

## Repository Layout 

- `data/`  
  Raw, machine-readable command output.

- `analysis/`  
  Derived metrics such as RTT summaries, hop counts, and packet loss calculations.  
  No screenshots. No narrative.

- `figures/`  
  Screenshots used only as visual confirmation. These do not replace raw data.

- `report/`  
 explanation of what was done, what was found, and why it matters.

This separation ensures conclusions can be independently verified.

---

## Key Findings

### Latency and Distance
- RTT increases predictably with geographic distance.
- Intercontinental paths introduce large, discrete RTT jumps visible in traceroute output.

### Packet Size Effects
- Small packets (1 byte) showed stable RTT and zero packet loss.
- Large packets (9000 bytes) experienced significant loss on paths that do not support jumbo frames.

### Path Visibility
- Some networks respond fully to traceroute probes.
- Others intentionally suppress ICMP responses near the destination, creating timeouts without implying loss of connectivity.

---

## Evidence and Traceability

Every claim in this project can be traced back to raw data:

- **Raw command output:**  
  See `data/`

- **Results and tables:**  
  See `analysis/network_analysis.md`

- **Visual confirmation (screenshots):**  
  See `figures/`

Screenshots are never used as primary evidence.  
If a screenshot exists, a corresponding raw text file exists first.

---

## Implications

This project demonstrates:
- my disciplined separation of observation, analysis, and narrative
- correct interpretation of ICMP behavior and limitations
- an approach aligned with professional debugging and postmortem workflows

The same structure scales naturally to larger performance investigations, outage analysis, or production network diagnostics.

---

## Notes

The original lab PDF is preserved at the repository root as a baseline artifact and was not modified.
