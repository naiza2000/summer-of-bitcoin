SUMMARY
1. [Attacking Bitcoin Core](https://btctranscripts.com/la-bitdevs/2020-04-16-amiti-uttarwar-attacking-bitcoin-core/)
 <br>  1. Consensus => nodes must agree on the same fundamental values. 
 <br>  2. Communication and interaction amongst nodes => P2P Network. 
 <br>  3. A successful P2P network is reliable, timely, accessible, private and upgradeable.
 <br>  4. Reliability -> prevention of network partitions. (might happen unintentionally - peer prioritization logic, intentional - double spend strategy, eclipse attack)
 <br>  5. Eclipse attack -> How to prevent it? a) increase number of connections but limited bandiwidth. b) choose diverse peers but limited information. c) run multiple nodes on different network interfaces but is user-independent. d) value long lasting connections. 
 <br>  6. 8 outbound + 125 total connections but privacy?
 <br>  7. Dynamic connections help maintain transaction privacy
 <br>  8. Three types of messages - addresses. transactions, blocks :
 <br>  9. Privacy vector attacks : a) send IP address, know its neighbours, b) timings of transaction propagation c) observing double spends
                                   d) forming chained mempool transaction and observing request behaviour of a node.  (To read more about it - Txprobe paper)
  <br> 10. To improve privacy : block-relay-only connection
                                   
