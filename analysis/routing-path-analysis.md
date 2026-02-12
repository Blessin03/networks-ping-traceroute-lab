## Path Length Comparison
UFL: 15 hops  
UQ: 19 hops  
UWI: Not reached. Last reply at hop 10  

UQ has a longer routing path than UFL. UWI did not complete the trace.

## RTT per Hop
UFL destination RTT: ~62 ms  
UQ destination RTT: ~337 ms  

More hops increase path length. Longer paths raise total RTT.

## ICMP Filtering Effects
The trace to UWI stopped after hop 10.

This suggests ICMP filtering. A firewall or security control likely blocked ICMP replies. The host may still be online, but it does not allow traceroute probes to reach it.
