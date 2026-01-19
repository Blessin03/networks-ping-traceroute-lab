# Network Analysis

This document summarizes ping and traceroute measurements collected for multiple destinations.  
All values are derived directly from raw output files stored in the `data/` directory.

---

## Ping Analysis

### University of Florida (UFL)

#### 1-Byte Packets
- **Source file:** `data/ping_ufl_1byte.txt`
- **Destination:** 128.227.36.35
- **Packets sent:** 20
- **Packets received:** 20
- **Packet loss:** 0%

**RTT Summary**

| Metric | Value |
|------|------|
| Minimum RTT | 60 ms |
| Maximum RTT | 79 ms |
| Average RTT | 62 ms |

**Observations**
- RTT values are stable with very little jitter.
- No packet loss observed.
- Suitable baseline for comparison with larger packet sizes.

---

#### 9000-Byte Packets
- **Source file:** `data/ping_ufl_9000byte.txt`
- **Destination:** 128.227.36.35
- **Packets sent:** 20
- **Packets received:** 9
- **Packet loss:** 55%

**RTT Summary (received packets only)**

| Metric | Value |
|------|------|
| Minimum RTT | 59 ms |
| Maximum RTT | 68 ms |
| Average RTT | 62 ms |

**Observations**
- More than half of the packets were lost.
- RTT for successful packets is similar to 1-byte packets.
- High loss strongly suggests MTU limitations and fragmentation or filtering of jumbo frames.

---

### University of Queensland (UQ)

#### 1-Byte Packets
- **Source file:** `data/ping_uq_1byte.txt`
- **Destination:** 130.102.184.3
- **Packets sent:** 20
- **Packets received:** 20
- **Packet loss:** 0%

**RTT Summary**

| Metric | Value |
|------|------|
| Minimum RTT | 335 ms |
| Maximum RTT | 345 ms |
| Average RTT | 337 ms |

**Observations**
- Significantly higher RTT due to long geographic distance.
- RTT values are very consistent, indicating a stable long-haul path.
- No packet loss observed.

---

## Traceroute Analysis

### University of Florida (UFL)
- **Source file:** `data/traceroute_ufl.txt`
- **Destination:** 128.227.36.35
- **Total hops:** 15

**Hop Summary**

| Hop Range | Notes |
|---------|------|
| 1–3 | Local network and ISP edge |
| 4–6 | Regional routing, RTT jumps to ~50 ms |
| 7–14 | Florida research/education backbone |
| 15 | Destination host |

**Observations**
- RTT increases sharply around hop 4, indicating exit from local region.
- No timeouts observed.
- Path is fully visible and stable.

---

### University of Queensland (UQ)
- **Source file:** `data/traceroute_uq.txt`
- **Destination:** 130.102.184.3
- **Last responding hop:** 19

**Hop Summary**

| Hop Range | Notes |
|---------|------|
| 1–6 | Local ISP and U.S. backbone |
| 7 | Timeout  |
| 8–10 | Transatlantic transit via London |
| 11–14 | Australian academic network |
| 15–18 | Multiple timeouts near destination |
| 19 | Destination responds |

**Observations**
- Large RTT jump between hops 10 and 11 marks intercontinental link.
- Multiple timeouts suggest ICMP rate limiting or firewall behavior.
- End-to-end connectivity is still intact.

---

### University of the West Indies (UWI)
- **Source file:** `data/traceroute_uwi.txt`
- **Destination:** 196.2.1.162
- **Last responding hop:** 10

**Hop Summary**

| Hop Range | Notes |
|---------|------|
| 1–6 | Local ISP and regional transit |
| 7–8 | Caribbean regional network |
| 9+ | No responses (persistent timeouts) |

**Observations**
- Destination network does not respond to traceroute probes.
- Timeouts do not necessarily indicate packet loss, only ICMP blocking.
- RTT remains relatively low before responses stop, suggesting proximity.

---

## Overall Conclusions

- Small packet pings show stable RTT and no loss across all tested destinations.
- Large packet pings experience severe loss when MTU limits are exceeded.
- Traceroute paths clearly reflect geographic distance and backbone transitions.
- ICMP filtering is common near destination networks, especially internationally.
