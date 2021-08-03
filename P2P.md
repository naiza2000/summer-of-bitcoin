SUMMARY
1. [Attacking Bitcoin Core](https://btctranscripts.com/la-bitdevs/2020-04-16-amiti-uttarwar-attacking-bitcoin-core/)
 <br>  1. Consensus => nodes must agree on the same fundamental values. 
 <br>  2. Communication and interaction amongst nodes => P2P Network. 
 <br>  3. A successful P2P network is reliable, timely, accessible, private and upgradeable.
 <br>  4. Reliability -> prevention of network partitions. (might happen unintentionally - peer prioritization logic, intentional - double spend strategy, eclipse attack)
 <br>  5. Eclipse attack -> How to prevent it? a) increase number of connections but limited bandiwidth. b) choose diverse peers but limited information. c) run multiple nodes on different network interfaces but is user-independent. d) value long lasting connections. 
 <br>  6. 8 outbound + 125 total connections but privacy? (two block-only relay connections have been added)
 <br>  7. Dynamic connections help maintain transaction privacy
 <br>  8. Three types of messages - addresses. transactions, blocks :
 <br>  9. Privacy vector attacks : a) send IP address, know its neighbours, b) timings of transaction propagation c) observing double spends
                                   d) forming chained mempool transaction and observing request behaviour of a node.  (To read more about it - Txprobe paper)
  <br> 10. To improve privacy : block-relay-only connection
  
  
2. [P2P with John Newberry](https://btctranscripts.com/scalingbitcoin/stanford-2017/edgeplusplus/p2p-john-newbery/)
  <br> 1. Connecting to the network : a) connect to seed network b) seed node tell us about other nodes using `ADDR` message. 
  <br> 2. `STANDARDNESS` applies only to the transactions outside the blocks. 
  <br> 3. Types of nodes : a) `Full Node` : full validating node. b) ` Pruned node ` : full node but is discarding the old blocks after it has validated them, as secure as the full node is. c) `Archival Nodes` : a full block that stores the entire history. d) `SPV Nodes` : Downloads the block headers and the information about specific transactions. These nodes can verify inclusion of the transaction using merkle tree proof, but they can't verify the exclusion. Can use `Bloom Filter`. 
  <br> 4. `-blocksonly` : full node, doesn't propagate transactions outside the block, `-nolisten` : won't accept incoming connections
  <br> 5. MESSAGE FORMAT :  `HEADER`+`PAYLOAD`, `24 bytes` long, `4 fixed bytes` - says that this is the message on bitcoin network, for main net, it is `f9beb4d9`, then `12 bytes` of command name => ASCII for what the command is, `4 bytes` for playload, then `checksum` - double sha-256 of the payload, then payload - max 32 MB
  <br> 6. MESSAGE TYPES : `control` and `inventory` messages, eg - `VERACK` is a control msg to exchange info about themselves to the other nodes. -> your node's version - 4 bytes, highest version that the transmitting node can connect to, then `service bits`(eg - NODE_NETWORK) , `INV` for transactions, `getdata` for demanding the transaction details. 
  <br> 7. BLOCK PROPAGATION - Should be as fast as possible. `FIBRE` - Parallel network. 
  <br> 8. `BIP 152`: SENDCMPCT message 
  The compact block includes the header - the 80 bytes as normal, has shortids(6-byte digest using this kind of this SipHash-2-4 algorithm) for the transactions, so those are 6-byte identifiers for the transaction saying. the receiving node from those shortids reconstructs a block based on transactions in its mempool. If it doesn’t have any,use the GETBLOCK TXN method, and the BLOCKTXN will send those remaining transactions.
 <br> 9. Mempool - uncomfirmed transactions. Default maximum mempool size is 300 megabytes.
 <br> 10. `BIP 133` - FEEFILTER; `BIP 125` OPT_IN REPLACE-BY-FEE - replace the old transaction with a new version with a higher transaction fee.
 
  
  
                                   
