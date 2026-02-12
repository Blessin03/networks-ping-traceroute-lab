# Limitations & Future Work

## ICMP Deprioritization
ICMP is often rate-limited.  
Routers and hosts may treat ICMP as low priority traffic.  
RTT can look worse than real application traffic.  
RTT can also look better if ICMP takes a different handling path.

## Single-Client / Single-ISP Bias
All tests ran from one machine.  
All tests used one ISP and one access network.  
Results may differ from other locations, ISPs, or devices.

## Time-of-Day Effects
Measurements came from one time window.  
Congestion changes over the day and week.  
Repeating the same tests over time would improve reliability.

## RTT Does Not Equal Throughput
RTT is the time for a packet to go to a host and return.  
Throughput depends on bandwidth, congestion, and TCP behavior.  
Low latency does not mean a high data rate.

## Future Work (TCP / UDP Tools)
- iperf for TCP throughput tests  
- UDP tests to measure loss and jitter  
- Path MTU discovery along the route  
- Repeated sampling over time windows  
