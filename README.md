# ZK-Circuit-Performance-and-Security-Data
To collect data on the performance and security characteristics of ZK circuits being verified on the Ethereum Blockchain and expose this data to users in a usable way.

## Background
For all of the benefits of smart contract based blockchains, they fundamentally suffer from two major limitations: Scalability and Privacy.  The TPS of Ethereum is currently 6 TPS https://ethtps.info/, and an astute data scientist can utilize the public chain data to see all transactions within the network. As Ethereum works to cross the chasm to mainstream adoption, zero knowledge proofs have emerged as a potential solution for both issues. For scalability, zk proofs are able to shrink the size of the data on chain by batching transactions and only posting a proof of what state change occured (rollups) or the merkle root of the new state (validiums).  Since the proof of the transactions validity is generated off chain and verified as correct via a smart contract, the size of the data is dramatically reduced.  On the privacy level, inputs to the zk proof can be kept seceret while still gauranteeing that they are valid.  With the complexity of these proofs, it is important to understand what trade offs are being made for the different types, hense this project.  Please see https://ethereum.org/en/developers/docs/scaling/zk-rollups/ and https://ethereum.org/en/developers/docs/scaling/validium/ for really good explainations for scaling using zk proofs.
## Methodology
How to collect the right data on zk circuits is a nuanced question.  While proofs themselves are providing the functionality, the important characteristics of the proof come from the circuit used to generate it.  For instance, there have been 143,627 proofs generated and verified by Tornado.cash's 10 ETH verifier (0xce172ce1f20ec0b3728c9965470eaf994a03557a).  All of these proofs have been generated off chain using the same circuit (https://github.com/tornadocash/tornado-core/blob/master/circuits/withdraw.circom) but, obviously, with different inputs. The proof is then converted into bytes and verified on chain with the verifier contract (0xce172ce1f20ec0b3728c9965470eaf994a03557a).
The issue with gathering data on circuits is that they are not posted on chain, and they are often not public.  Since this project is aimed at the use of zk tech on Ethereum, the best proxy for circuits is actually the verifying contract.  Each change to a circuit requires a change to its verifier, making this is a good way to gain data on unique circuits, and collect the data on the verifications happening.



