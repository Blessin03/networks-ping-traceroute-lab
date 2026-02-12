## Large Packet Test
When I sent 9000-byte packets to www.ufl.edu, more than half failed. RTT did not increase compared to the 1-byte test.

## Packet Loss
Packet size: 9000 bytes  
Packets sent: 20  
Packets received: 9  
Packet loss: 55%  

1-byte average RTT: 62 ms  
9000-byte average RTT: 62 ms  
RTT difference: 0 ms  

Large packets showed heavy loss but similar RTT on successful replies.

## MTU and Fragmentation
Most networks use an MTU near 1500 bytes. A 9000-byte packet exceeds this limit.

The network must fragment the packet. If one fragment drops, the full packet fails. Some routers drop oversized packets instead of fragmenting them.

This explains the 55% packet loss.
