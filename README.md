# Chain-Learning
Repository to keep track of self learning in blockchain domain
# Day 1:

# The Merge
Ethereum Mainnet uses proof-of-stake, but this wasn't always the case.
The upgrade from the original proof-of-work mechanism to proof-of-stake was called The Merge.
The Merge refers to the original Ethereum Mainnet merging with a separate proof-of-stake blockchain called the Beacon Chain, now existing as one chain.
The Merge reduced Ethereum's energy consumption by ~99.95%.

# Decentralized finance (DeFi) Intro
A global, open alternative to the current financial system.
Products that let you borrow, save, invest, trade, and more.
Based on open-source technology that anyone can program with.

# Ether
Ether (ETH) is the cryptocurrency used for many things on the Ethereum network. Fundamentally, it is the only acceptable form of payment for transaction fees, and after The Merge, ether is required to validate and propose blocks on Mainnet. Ether is also used as a primary form of collateral in the DeFi lending markets, as a unit of account in NFT marketplaces, as payment earned for performing services or selling real-world goods, and more.

# Mining Ether
Minting is the process in which new ether gets created on the Ethereum ledger.
Ether is minted as a reward for each block proposed and at every epoch checkpoint for other validator activity related to reaching consensus. The total amount issued depends on the number of validators and how much ether they have staked. This total issuance is divided equally among validators in the ideal case that all validators are honest and online, but in reality, it varies based on validator performance. About 1/8 of the total issuance goes to the block proposer; the remainder is distributed across the other validators

# What is meant by proposer in mining?
An Ethereum entity that adds the next block of transactions to the blockchain. It used to be a "miner" but changed to a "proposer" in 2022 when Ethereum switched from proof-of-work to proof-of-stake. Miners became validator proposers and validators became validator attesters.
In Pow You can refer to a mining participant/machine who guess the most closest or equal solution to given problem. In POS proposer refers to participant who is a validator and have stacked minimum coins required to be a validator. i.e 32 eth in case of etherium.

# BURNING ETHER
Ether burn occurs in every transaction on Ethereum. When users pay for their transactions, a base gas fee, set by the network according to transactional demand, gets destroyed. This, coupled with variable block sizes and a maximum gas fee, simplifies transaction fee estimation on Ethereum. When network demand is high, blocks can burn more ether than they mint, effectively offsetting ether issuance.

# Benefits OF Burning Ether
Burning the base fee prevents various ways block producers could manipulate it otherwise. For example, if block producers received the base fee, they could include their own transactions for free and raise the base fee for everyone else. Alternatively, they could refund the base fee to some users off-chain, leading to a more opaque and complex transaction fee market.

