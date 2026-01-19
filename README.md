# Network Behavior Investigation: Ping and Traceroute

## 1. Problem Statement

This project investigates how network behavior changes across geographic distance, routing paths, and packet size. Using ICMP-based measurements, it examines latency, packet loss, and hop visibility to different international destinations. The goal is to observe how real networks behave under simple but telling probes, and to surface behaviors that matter in production environments, such as MTU limits and ICMP filtering.

---

## 2. Tools & Protocols Used

- `ping` (Windows)
- `tracert` (Windows)
- ICMP (Echo Request / Echo Reply, Time Exceeded)
- Windows networking stack

---

## 3. Methodology (High-Level)

- Sent repeated ICMP echo requests with **small (1 byte)** and **large (9000 byte)** payloads
- Targeted multiple destinations with increasing geographic distance
- Used traceroute to map hop-by-hop routing paths
- Captured raw command output verbatim for analysis
- Derived metrics (RTT, hop counts, packet loss) from raw data only

All tests are deterministic in structure and can be rerun under similar conditions.

---

## 4. Key Findings

- RTT increases predictably with geographic distance (regional vs intercontinental paths)
- Large packets experienced **55% packet loss** on paths that do not support jumbo frames
- Successful large-packet RTTs were similar to small packets, indicating loss was not congestion-related
- Traceroute revealed clear intercontinental hops with large latency jumps
- Some destination networks (e.g., UWI) suppress ICMP responses, resulting in traceroute timeouts without loss of connectivity

---

## 5. Repository Structure

- `data/` - command outputs
- `analysis/` - observations based on raw data
- `figures/` - screenshots 
- `report/` - longer-form narrative and context
- `lab-report-original.pdf` - original  doc

---

## 6. How to Reproduce

**Assumptions**
- Windows OS
- Unrestricted outbound ICMP
- Results will vary based on location and network conditions

```
ping www.ufl.edu -n 20 -l 1 
ping www.uq.edu.au -n 20 -l 1 
ping www.ufl.edu -n 20 -l 9000 

tracert www.ufl.edu 
tracert www.uq.edu.au 
tracert www.uwi.edu 
```