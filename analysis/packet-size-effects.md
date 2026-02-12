## Large Packet Test
When I sent 9000-byte packets to www.ufl.edu, more than half failed. RTT also increased compared to the 1-byte test.

## Packet Loss
Packet size: 9000 bytes  
Packets sent: 20  
Packets received: 9  
Packet loss: 55% :contentReference 

1-byte average RTT: 63 ms  
9000-byte average RTT: 80 ms  
RTT difference: +17 ms :contentReference  

Large packets showed clear loss and higher delay.

## MTU and Fragmentation
Most networks use an MTU near 1500 bytes. A 9000-byte packet exceeds this limit.

The network must split it into fragments. If one fragment drops, the whole packet fails. Some routers also drop oversized packets instead of fragmenting them.

This explains the 55% loss and the higher RTT.
