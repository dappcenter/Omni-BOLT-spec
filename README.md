# OmniBOLT: In-Progress Specifications
[![](https://img.shields.io/badge/license-MIT-brightgreen)](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/LICENSE) [![](https://img.shields.io/badge/made%20by-Omni%20Foundation-blue)]() [![](https://img.shields.io/badge/project-LightningOnOmni-orange)](https://github.com/LightningOnOmnilayer/LightningOnOmni)

* `Contact`: Neo Carmack(neocarmack@omnilab.online), Ben Fei(benfei@omnilab.online)

Based on the fundamental theory of Lightning network, OmniBOLT specification describes how to enable OmniLayer assets to be transferred via ligtning channels, and how can OmniLayer assets benefit from the noval quick payment theory. According to the layer-2 protocol [BOLT (Basis of Lightning Technology) ](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md) specification for off-chain bitcoin transfer, we propose this OmniLayer specific protocol to expand the horizons of the basic theory, to support wider perspective of assets.    

We name this new specification OmniBOLT, in order to avoid possible conflicts with BOLT. We break down our task into two major steps:  

>the first step, we run nodes that are omni assets aware: for example, users can creat channels for USDT, which is issued on Omnilayer and BTC netowrk, then they will be able to transfer USDT more quick and more cheaper.  

>the second step, we will try to be compatible with existing Lightning Nodes around the world, and we sincerely invite experts working on BOLT to work together with us.  

OmniBOLT itself does not issue tokens. All tokens are issued on Omnilayer, and enter the OmniBOLT network through P2(W)SH backed channels, being locked on the main chain, and can be redeemed on the Omnilayer main chain at any time.  

To be self-contained, for any messages or definitions that differ from what are defined in original BOLT specification, we will include both new and old arguments to form complete messages. For those messages that are the same to BOLT, we just link to the original address where they are defined.    

# Advantages

Not only BTC instant payment is supported as current implementation of lightning network, but also:  
 
* Instant payment of smart assets issued on OmniLayer. 
* Cross channel atomic swap of different assets.
* Decentralized exchange on top of lightning channels with quick exchange speed. 
* Collateral Lending Contract based on atomic swap.
* More flexible contracts for DeFi. Interested readers shall directly go to [chapter 6: DEX, Collateral Lending Contract, online store ...](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-06-Mortgage-Loan-Contracts-for-Crypto-Assets.md) to seek more examples.

# OmniBOLT Terminology

* `OBD`: OmniBOLT Daemon.
* `channel`: A channel refers to Poon-Dryja channel in ligtning network. Channel is denoted by `[Alice, USDT, Bob]`, which means Alice and Bob build a channel and fund it by USDT.
* `property`: refers to tokens issued on Omnilayer, the same to "asset".
* `RSMC`: Revocable Sequence Maturity Contract is composed to punish malicious peers, who broadcasts elder commitment transactions to get more refund than what's exactly in his balance.
* `HTLC`: Hashed Time-Lock Contract chains multiple channels for transferring tokens from one peer to another, betweem whom there is no direct channel established.
* `Commitment Transaction`: is created but not broadcast, and may be invalidated by next commitment transaction.
* `BR`: Breach Remedy transaction is used in RSMC, that if Alice cheats by broadcasting an elder commmitment transaction, BR will send all her money to Bob.
* `RD`: Revocable Delivery transaction pays out from the 2-2 P2SH transaction output, when Alice broadcast the latest legitimate commitment transaction. It sends money to Bob immediatly and will send money to Alice after relatively, say 100 blocks, from current block height. 
* `HED`:  HTLC Execution Delivery
* `HT`: HTLC Timeout
* `HBR`: HTLC Breach Remedy, the breach remedy transaction in HTLC
* `HTRD`: HTLC Timeout Revocable Delivery, the revocable delievery transaction in HTLC
* `HTBR`: HTLC Timeout Breach Remedy, punishes Alice who broadcasts the elder hash time-locked transaction during the time lock period. 
* `Atomic Swap`: Atomic swap technology enables the exchange of one cryptocurrency for another without using centralized intermediaries, such as exchanges. 
* `HTLSC`: Hashed TimeLock Swap Contract, which consists of two seperate HTLCs with extra specified exchange rate of tokens and time lockers.


# Chapters

We not only just list messages and arguments that are used in our implementation, we also complete content that explains why we do so. Most of this spec is strictly follow the rules/logics defined in the lightning white paper. The original paper may be hard to read for our programmers, so we draw some diagrams for better understanding. Hope it helps :-)

OmniBOLT #01: Base Protocol

[OmniBOLT #02:](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-02-peer-protocol.md) peer-protocol, Poon-Dryja channel open

[OmniBOLT #03:](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-03-RSMC-and-OmniLayer-Transactions.md) RSMC and OmniLayer Transactions 

[OmniBOLT #04:](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-04-HTLC-and-Payment-Routing.md) HTLC and payment Routing

[OmniBOLT #05:](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-05-Atomic-Swap-among-Channels.md) Atomic Swap Protocol among Channels

[OmniBOLT #06:](https://github.com/LightningOnOmnilayer/Omni-BOLT-spec/blob/master/OmniBOLT-06-Mortgage-Loan-Contracts-for-Crypto-Assets.md) DEX, Collateral Lending Contract, online store and more applications

OmniBOLT #07: Construct transactions on OmniLayer

# Implementation and API for wallet

Implementation of OmniBOLT specification can be found in this repository [LightningOnOmnilayer](https://github.com/LightningOnOmnilayer/LightningOnOmni), as well as the API online documentation can be found [here](https://api.omnilab.online).

Javascript API: [here](https://github.com/LightningOnOmnilayer/DebuggingTool/blob/master/js/obdapi.js).

GUI debugging tool: [here](https://github.com/LightningOnOmnilayer/DebuggingTool).


# Contribution

OmniBolt specification is initiated by [Omnilayer.foundation](https://github.com/OmniLayer).
Any proposal, please submit issues in this repo.
