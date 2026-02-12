## Observed Latency
UFL average RTT: 62 ms  
UQ average RTT: 337 ms  

Traceroute shows 15 hops to UFL  
Traceroute reaches UQ in 19 hops  

UQ has much higher latency than UFL.

## Distance and Propagation Delay
UFL is closer in geographic distance. The signal travels a shorter path, so propagation delay is lower.

UQ is in Australia. The signal crosses long international links. Greater distance increases propagation delay. More hops add processing time along the path.

## Observed Variability
Both hosts returned all 1-byte packets with 0% loss.  

RTT stayed within a narrow range. Small changes come from normal queuing delay at routers. The main cause of the difference is distance.

| Host              | Packet Size (bytes) | Sent | Received | Loss (%) | Min RTT (ms) | Avg RTT (ms) | Max RTT(ms) |
|-------------------|---------------------|------|----------|----------|--------------|--------------|--------------|
| www.ufl.edu       | 1                   | 20   | 20       | 0        | 60           | 62           | 79           |
| www.ufl.edu       | 9000                | 20   | 9        | 55       | 59           | 62           | 68           |
| www.uq.edu.au     | 1                   | 20   | 20       | 0        | 335          | 337          | 345          |

