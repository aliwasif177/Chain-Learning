# Chain-Learning
Repository to keep track of self learning in blockchain domain. 

# Day 29:



# Day 28:

# Finality delay:
A finality delay attack prevents the network from reaching the necessary conditions finalizing sections of the chain. Without finality, it is hard to trust financial applications built on top of Ethereum. The aim of a finality delay attack is likely simply to disrupt Ethereum rather than to directly profit, unless the attacker has some strategic short position(s).

# Day 27:

# Double finality:
Double finality is the unlikely but severe condition where two forks are able to finalize simultaneously, creating a permanent schism in the chain. This is theoretically possible for an attacker willing to risk 34% of the total staked ether. The community would be forced to coordinate off-chain and come to an agreement about which chain to follow, which would require strength in the social layer.

# Day 26:

# Reorg:
A “reorg” is a reshuffling of blocks into a new order, perhaps with some addition or subtraction of blocks in the canonical chain. A malicious reorg might ensure specific blocks are included or excluded, allowing double-spending or value extraction by front-running and back-running transactions (MEV). Re-orgs could also be used to prevent certain transactions from being included in the canonical chain - a form of censorship. The most extreme form of reorg is “finality reversion” which removes or replaces blocks that have previously been finalized. This is only possible if more than ⅓ of the total staked ether is destroyed by the attacker - this guarantee is known as “economic finality” - more on this later.   

# Day 25:

# Aggregator in attestation:
The aggregator collects all the attestations it hears about over the gossip network that have equivalent data to its own. The sender of each matching attestation is recorded in the aggregation_bits.  


# Day 24:

# Weak Subjectivity:
Inherenet of POS in blockchain to help validators select correct chain in case of multiple legit forks.  



# Day 23:

# What is Gasper:
Gasper is combination of Casper Friendly Finality Gadget (Casper-FFG) and fork choice algorith LMD-Ghost. Togather this combination form the consensus mechanism securing Proof Of Stake. Casper is mechanism that upgrades finalized block to the chain so that incoming blocks may decide on which they should go based on accumulative weighate of attested blocks. 

# Role Of Gasper:
- Sits on top of POS where nodes stake thier eth. Basically it is the holder of thier eth as a security and it can burn destroy thier eth in case of dishonesty and laziness.  
- Responsible for entrance of new blocks in chain. 
- Responsible for the fork choice algortihm i.e in case of multiple chains/branches where should a block needs to be attached. 

# Finality:
Property of block which means a block cannot be reverted unless a critical consensus faliur or 1/3rd of total staked ether destroyed by attacker.  

# How a block is finalized:
Block is finalized in two steps.  
- 2/3rd of the total staked ether must have voted in fvour of that block to get attached in cannonical chain. This conditions upgrade block to justified block.   
- When another block is justified on top of this block then it will become the finalized block. It cannot be changed by attacker unless he spends millions of ether i.e billions of usd. 

# Requirments of finality:
Finality requires a two-thirds agreement that a block is canonical, an attacker cannot possibly create an alternative finalized chain without:

- Owning or manipulating two-thirds of the total staked ether.  
- Destroying at least one-third of the total staked ether.  

# Plausible liveness:
This is the condition that as long as two-thirds of the total staked ether is voting honestly and following the protocol, the chain will be able to finalize irrespective of any other activity (such as attacks, latency issues, or slashings).

# Inactivity Leak:
This mechanism activates when the chain has failed to finalize for more than four epochs. The validators that are not actively attesting to the majority chain have their stake gradually drained away until the majority regains two-thirds of the total stake, ensuring that liveness failures are only temporary.  


# Day 22:

# PROOF-OF-STAKE AND SECURITY:

In POS when attacker wants to attack he needs 51% of total staked and lets say if he get this 51% successfully and make the fork of their own choice by accumaltive weightate sum of attestaion on cannonical chain. But in POS gives privilages to validators. If an honest validator sniff something wrong he can vote in favour of minority/short chain and encourage other app and pools to do. they can also forcibly remove attacker from network. This way POS is more secure than POW even the attacker gets 51% of staked eth.  

# Selection of validator node:
it is based on main factors i.e block hash, node wealth and staked eth by that node. 
there are two main algorithms to determine the validator. 
- Randomized Block Selection
- Coin age selection. 

# Randomized Block Selection:
Validators for forging are selected on base of the combination of lower hash value and staked eth by that node. 

# Coin age selection:
validaors for forging are selected on basis of the duration of thier stacked eth and amount of stacked eth. This algorith work by mathematical equation.  

forger = number of days coins have been stacked by that validator * amount of coins stacked by that validator.  

Once it has forged a block then its days (coin age) will be reset to zero this way all validators gets thier turn to be a forger.  This reset prohints the large validators with old age and good amount to dominate the chain. 


# Day 21:

# How to be validator in POS:
For becoming a validaor a node needs to run three layers of software. 
- Execution Client
- Consensus Client
- Validator. 

And node must stake 32 eth in seposit contract. After that it will be added to the validator queue list which is miantained to limit number of validators. Once activated. You become validarotthen as a validator you will recieve the block from peer network. Then validator will reexecute all transactions in block and verifies block signature and then cast a vote in favour of that block which is known as attestation and over netwok.   

# Finality in blockchain:
Finality is when a transaction is part of block which cannot be changes without burning a significant amount of eth. 

# Epoch:
In POS we have slots and slot contains 12 seconds in which a validator is chosen radomly and block has been moved forward for attestaion and linking in chain and epoch is equal to 32 slots. 

- 1epoch = 32 slots = 12*32 = 384.   

# Checkpoint:
checkpoint refers to first block in every epoch. Validators vote for the pair of checkpoint blocks which are considered to be valid. of most validators favour in pair of checkpoint block pairs then this become the target checkpoin blocks and these become justified. NOw this checkpoint target become the finalized block and it cannot be reverted. To revert it one must burn atleat 1/3rd of total eth staked on ethereum chain and if attackers do this then by rule we need two 3rd of total validators which cannot be done. 
And if the chain fails to finalize a block with more than 4 epochs then in In these attacks blockchain will simply bleed away all the staked ethereum of nodes voting against the majority. 

# Crypto ecomnomic security:
Once the node becomes a validator. He needs a good hardware and staked eth then he will validate blocks. when a validator validates block then its stake will increase on every validation.

# Chances of slasing of validators in POS:
If validaor is not validating when required and it happens often then chain sniff it as cognative attack and penalty will be thrown because attackers can attack this way. this penality is in form of slashing. Slashing of eth depends on how many validators are being slashed. its compound effect is huge but of you are single node on your own then it will be very minimal almost 1% of toatl eth staked by that node or 100% if it is compound slashing of multiple validators.  

# Reasons of slashing of validaors in POS:
Primarily there can be 2 main reasons of slashing. 
# 1 equivocating:
propsing multiple blocks in single slot. 
- Submitting contradictory attestaions. 

# Penalities Order:

- Imediate penality on day 1 0.5 eth. 
- corelated penality that could be upto 100%. 
- kicked out of network. 

# Fork choice:
In chain there is only one block at head of chain. So when a new block is proposed, validated and attested and when it is going to be attached it can see multiple chain i.e heads of chain. Now this block will decide which is the wrong or right turn .In these conditions consensus client perform an algorithm known as LMD_GHOST to verify the correct fork. basically kt verifies fork by the weigtage of attestion in hostory for respective fork.  


# Day 20:

# Energy usage of POW:
 The main criticism faced by POW was energy consumed by miners machine to validate blocks. which was nearly equal to  about 70 TWh/yr (about the same as the Czech Republic - according to digiconomist on 18-July-2022).
 
 # Etash:
 Once used by etherium for mining. In this algorithm miner tries to find nonce input by brute force and as they able to find very close number to the given threshhold. They get rewards. This way resultant hash is smaller tan ciomputing difficulty.  
 
 # DAGGER HASHIMOTO
 
 

# Day 19:

missed

# Day 18:
Noting to note

# Day 17:
Noting to note

# Casper:




# Day 16:
Noting to note

# Frontburning:

# Slashing risk:

# Sharding:  


# Day 15:

# Consensus mechanisms (3 types):
- Proof of work. 
- Proof of stake. 
- proof of authority.   

# Sybil attack:
type of attack in which individual or group of individulas subverts insformation by creating multuple identitites of himself and gain large percentage of network. 

# prevention of sybil attack:
prevented by Sybil resistance mechanism i.e POW and POS. these mechanism does not allow user to create multiple identities by making user pay gas fee and spend lot of energy in ecnomic form. So if someone tries to attack he would get nothing but lose of his crypto coins.    

# Chain selection rule:
used to decide which is the correct one. bitcoin uses the lonest chain rule. 

# Frok-choice algorithm:
dertermine chain by weight of chains. weigt means the sum of validator votes weighted by thier stacked ether balance.  

# Longest chain rule:
means whichever the blockchain is longest will be accepted by nodes. In POW the longest chain is determined by total accumulative sum of chian's proof of work puzzle difficulty.    


# Day 14:

# Networks:
- Mainnet ( POW or POS). 
- Testnet (Proof Of Authority). 

# Proof Of Authority:
Only applicable in testnet for validating and mining transaction. 
before meger POA choses some random miners to validate transactions and blocks on testnet. Since there is nothing to stake on testnet. So they stacke thier identity in order to be a validator. 

# Which testnet should I user?
# Sepolia testsnet for Apllication development (uses POS):
for application developemnt i.e Dapp. you should use sepolia. Since it is new and performs rapid and efficient transactions over network.  

- Closed validator set, controlled by client & testing teams. 
- New testnet, less applications deployed than other testnets. 
- Fast to sync and running a node requires minimal disk space.  

# Goerli for tesing of validating and stacking (uses POS):
when etherum protocols get upgrades then any user can use this testnet to test the new upgrades in protocols and then deopending on cost and effecieny can move to mainnet.   
- Open validator set, stakers can test network upgrades. 
- Large state, useful for testing complex smart contract interactions. 
- Longer to sync and requires more storage to run a node.   

# Consortium networks:
The consensus process is controlled by a pre-defined set of nodes that are trusted. For example, a private network of known academic institutions that each govern a single node, and blocks are validated by a threshold of signatories within the network.  

If a public Ethereum network is like the public internet, a consortium network is like a private intranet.  

# Consensus: 
consensus means that at least 66% of the nodes on the network agree on the global state of the network.  

# Day 13:

# Node architecture:

consist of execution client and consensus client.  
In POS execution client needs to work along consensus client to be a valida node.  
Both clients are connected to thier respective netwoks in p2p network enabling both client to mange thier transaction pool and then communicate with each other though engine api.

<img width="1920" alt="image" src="https://user-images.githubusercontent.com/60692401/208646337-ac646e74-0864-40ec-94a9-83f8b9d926c1.png">

Consensus client use eninge api to pass bundle of transactions to execution client. When consensus clients needs to add a new block it will communicate with execution client and request for transaction responsing to that block.  

# What doest execution client do?
Execution client is responsible for transaction ghossips across its p2p network and updating evm but cannot play block ghossips as it is consensus client responsibilty. e.g when a trsaction execute executes from bynance the execution client will be first one to listen to that transaction and pass it across other nodes across p2p network.  
The execution client is also responsible for re-executing transactions in new blocks to ensure they are valid.  

In summary, the execution client is:

- a user gateway to Ethereum
- home to the Ethereum Virtual Machine, Ethereum's state and transaction pool.


# What does consensus client do?
Consensus client is responsible for keeping all the nodes synced with evm block states and perfoems forking algorith depending on user balances and longest chain to make sure that all blocks are connected to right chain.   
The consensus client does not participate in attesting to or proposing blocks - this is done by a validator, an optional add-on to a consensus client. A consensus client without a validator only keeps up with the head of the chain, allowing the node to stay synced. This enables a user to transact with Ethereum using their execution client, confident that they are on the correct chain.

# Validators:
Validator comes from consensus client if node opertaor stake 32 eth on thier consensus client then they will be add validator on thier consensus client. 
The validator handles attestations and block proposals. They enable a node to accrue rewards or lose ETH via penalties or slashing. Running the validator software also makes a node eligible to be selected to propose a new block.

# Node components comparison:

<img width="1920" alt="image" src="https://user-images.githubusercontent.com/60692401/208650933-590bf8f4-de75-4371-b159-ae2ebf89e39c.png">



# Day 12:

# Client diversity:

when nodes are setup. they can be setup on two layer i.e execution layer and consensus layer. But for executing these layers securoty is very important. A client shou;d have traffic of nodes upto 33%. Because if attackers attack on a client i.e geth prysm etc. it can corrupt thaty client. So to bare minimum lose we should have minority nodes on this client. So minimum slashing occurs on the nodes./ validators because slashing of validatotrs is propoptional to traffic on that client.

Addressing client diversity requires more than individual users to choose minority clients 
- it requires mining/validator pools and institutions like the major dapps and exchanges to switch clients too.   

# Solo stacking:
In solo stacking a machine/node must run both client on his own machine after the merge. But before merger it was possible for node to run only the execution or consensus layer. 

# Node servcies:

includes moralis, alchemy and chainstack etc. 



# Day 11:

# Minimum requirements to set up a node:

# Minimum requirements
- CPU with 2+ cores
- 8 GB RAM
- 700GB free disk space
- 10+ MBit/s bandwidth

#  Recommended specifications

- Fast CPU with 4+ cores
- 16 GB+ RAM
- Fast SSD with 1+TB
- 25+ MBit/s bandwidth

# List of execution clients:

- Besu
- Erigon (Doesn't provide a pre-built binary, has to be compiled)
- Geth
- Nethermind

# List of consensus client:

- Lighthouse
- Lodestar (Doesn't provide a pre-built binary, only a Docker image or to be build from source)
- Nimbus
- Prysm
- Teku. 

# Day 10

Got nothing to note


# Day 9:

# Slashing:
Slashing describes the process whereby other network participants forcibly eject an offending validator from the Beacon Chain while continuously draining their balance. In the most extreme cases, a slashed validator may lose their entire stake in the network.

# Corelated slashing:
In paladakot and eth2 chain maintain correlated slashing. This means that the penalty escalates based on the percentage of total validators that engage in the bad behavior at the same time. Let’s say that 10 out of 100 validators are down. In such a case, the slashing penalty is smaller per validator than if 25 out of 100 validators are down.



# Day 8:


# Syncronization in etherium:
refers to syncing of state brought up by node into evem state. Syncing takes time depending on node and syncing strategy.

# Full node:
stores full blockchain data i.e evm state, blocks and trasactions along with thier data and hashes to prevoius blocks. fetch data on request and it may be pruned. All states can be derived from a full node ( even the old ones can be reconstyructed from the derived transactions). 

# Light node:
you can say they are derived from the full node. Unlike full node, they dont download the full block data. They download headers of block and we know from header data through encryption we can get all data. In case we want a full block data from light node then we can request a full node correspond to that light node this way we can fetch the whole data on request. this is faster than full nodes with same security.   
Light node cannot participate in consensus to become validator/proposer/attester since these roles require the whole blockchain data for adding new blocks.  
Light nodes often fail to find peer data.   

# Archieve node:
- Stores everything kept in the full node and builds an archive of historical states. It is needed if you want to query something like an account balance at block #4,000,000, or simply and reliably test your own transactions set without mining them using tracing.  
- Syncing clients in any mode other than archive will result in pruned blockchain data. This means, there is no archive of all historical states but the full node is able to build them on demand.  

# Dont trust, verify:
if you run your machine as node in distributed ledger then you dont need to trust other nodes to verify your transactions. Since you are running ethererum client on your machine the you can verify the transaction on your own without trusting network.    



# Day 7:


# Merkle tree:
A bindary tree that keeps track of transaction and blocks in form of hashes. So, when a node tries to vareify transaction/block. it dont need to have complete state copy of bitcoin/etherium. tree stores hasghes of transactions and keep hashing the combination of all transaction while narrowing it down to one single transaction i.e leaf node. which pocess trasnsaction id.   

Consider the following scenario: A, B, C, and D are four transactions, all executed on the same block. Each transaction is then hashed, leaving you with:   

Hash A. 
Hash B. 
Hash C. 
Hash D. 
The hashes are paired together, resulting in:   

Hash AB. 
and. 

Hash CD. 
And therefore, your Merkle Root is formed by combining these two hashes: Hash ABCD.



<img width="1214" alt="image" src="https://user-images.githubusercontent.com/60692401/207318359-a02acd35-79f3-466d-9b91-d82da38b9210.png">




# Day 6:

# Block time:
In network when lrage number of transactions bundled up then it is time to make blocks and seperate them and then link to chain. So for tis validator needs to propose a block. In network after every 12 seconds they proposes a block and these 12 seconds are called slot. Sometime max nodes/machines might be offline and network can let go that slot empty because it corresponds to that offline validator.

# Block size:
Each block in network chain has a limited size of 15 million gas. But It can be expand or shrink based on requirments. At max block can hold transaction of 30 million gas (2x of initial limit). Accumulative gas of transactions should always be less than the limit.  
If we have a block size of more than 30 million it will have extra large size then it will be difficult to validate this for low performant node and thus time taking and require more power consuption.  




# Day 5:

# Nodes:
Machines that are running on Ethereum network that are responsible for verifying blocks and transactions and it coukd be attester, validator or proposer. These machines can be miner and other machines that participate in keeping network. But after merge a node cannot execure on its own. It needs consensus client ( which staked coin ) to work with.  

# Execution client:
Refers to the nodes that were involved in POW in eth1 responsible for keeping track of new transactions updating database and evm state by connecting and aggregation to all other nodes acroos network.  

# Consensus client:
Refers to client/node which have stacked chain coins in order to propose the block/transaction passed on from execution client.  



# Day 4:


# EIPI Typed Transaction Enevelope:
contain two main payload in transaction.  
- Transaction type ( a number btw 0 to 0*7f for total 128 typess of transactions). 
- Transaction payload ( arbitrary byte array of data based on selected transaction type btw 0 - 0*7f). 

# Block:
Blocks are bactches of transaction. when there are limited number of trabnsaction occurs on network. network make a collection/bactch of these transactions and constitute a block.  
In chain all blocks are linked togather by keeping the hash of prevoius block and then produce combine hash of previous block own data and then pass this hash address to next block. 
So in this way if one block data chhanges its hash will change and subsequently all blocks in chain will invalidate this change.    



# Day 3:


# Transaction:
transaction has 4 basic elements
- Recipient
- Signature
- Nonce
- Value
- Data
- Gas Limit
- Max Priority Fee Per Gas (tip to validator)
- Max Fee Per Gas (inclusive of baseFeePerGas and maxPriorityFeePerGas)

# Transaction Structure:
- Transaction request on network using Geth. 
Request. 

{
  from: "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
  to: "0xac03bb73b6a9e108530aff4df5077c2b3d481e5a",
  gasLimit: "21000",
  maxFeePerGas: "300",
  maxPriorityFeePerGas: "10",
  nonce: "0",
  value: "10000000000"
}

Response. 

response = {
  "jsonrpc": "2.0",
  "id": 2,
  "result": {
    "raw": "0xf88380018203339407a565b7ed7d7a678680a4c162885bedbb695fe080a44401a6e4000000000000000000000000000000000000000000000000000000000000001226a0223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20ea02aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",
    "tx": {
      "nonce": "0x0",
      "maxFeePerGas": "0x1234",
      "maxPriorityFeePerGas": "0x1234",
      "gas": "0x55555",
      "to": "0x07a565b7ed7d7a678680a4c162885bedbb695fe0",
      "value": "0x1234",
      "input": "0xabcd",
      "v": "0x26",
      "r": "0x223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20e",
      "s": "0x2aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",
      "hash": "0xeba2df809e7a612a0a0d444ccfa5c839624bdc00dd29e3340d46df3870f8a30e"
    }
  }
}. 

Where raw is the signed transaction in encoded form. And tx=== json.parse(responsse.raw). This way we can get signature to verify the sender i.e tx.hash===signature hash which will then be passed to eliptic curve to discover public key of sender for verification.   



# Day 2:
  
# Accounts:
An Ethereum account is an entity with an ether (ETH) balance that can send transactions on Ethereum. Accounts can be user-controlled or deployed as smart contracts.

# Types Of Accounts:
-Externally-owned account (EOA) – controlled by anyone with the private keys. 
-Contract account – a smart contract deployed to the network, controlled by code. 

# Constitution Of Account:
-Nonce
-Balnce
-CodeHash
-storageRoot

# nonce:
A counter that indicates the number of transactions sent from the account. This ensures transactions are only processed once. In a contract account, this number represents the number of contracts created by the account.  

# Balance:
The number of wei owned by external account or contract account.  

# CodeHash (code of an account):
A deployed contract account composed of code fragments that runs on EVM. EVM store all these code fragments under the state database in thier respective hashes and later use these hashes for retrieval of that code chunks to perform some transactions on message call. It can not be changed. Even if you update your contract code then it will be a new transaction and old codehash resides there constantly. For externally owned accounts, the codeHash field is the hash of an empty string. 

# storageRoot:
Sometimes known as a storage hash. A 256-bit hash of the root node of a Merkle Patricia trie that encodes the storage contents of the account (a mapping between 256-bit integer values), encoded into the trie as a mapping from the Keccak 256-bit hash of the 256-bit integer keys to the RLP-encoded 256-bit integer values. This trie encodes the hash of the storage contents of this account, and is empty by default.  

# ACCOUNT CREATION:


# ECDSA: Elliptic Curve Signatures:
Algotiyh used to recover public key from private key. ECDSA keys and signatures are shorter than in RSA for the same security level. A 256-bit ECDSA signature has the same security strength like 3072-bit RSA signature.

# Public Key Generqation Using ECDSA:
The ECDSA key-pair consists of:   
-private key (integer): privKey.    
-public key (EC point): pubKey = privKey * G.  
    
      
The private key is generated as a random integer in the range [0...n-1]. The public key pubKey is a point on the elliptic curve, calculated by the EC point multiplication:   
-pubKey = privKey * G (the private key, multiplied by the generator point G).
The public key EC point {x, y} can be compressed to just one of the coordinates + 1 bit (parity). For the secp256k1 curve, the private key is 256-bit integer (32 bytes) and the compressed public key is 257-bit integer (~ 33 bytes).  

# Keys in Proof Of Stake Ethereium:
- Public key
- Private key
# Validator keys  => public and Private and both uses Boneh-Lyn-Shacham (BLS) signature scheme
( To reach at consensus all validators needs to communicate with each other. Each validator msg aggregates across all other validators. And communication of msgs/transactions btw large number of validators result in more network consumption and slow transactions. So to make this aggregation of msgs rapid validatore keys have been introduces ). 
# Withdrawl keys => public and Private and both uses Boneh-Lyn-Shacham (BLS) signature scheme
 And now if these two new keys are introduces then for sure they also require some kind of key pair cryptography mechanism and for that purpose Etherium uses Boneh-Lyn-Shacham (BLS) signature scheme

# Boneh-Lyn-Shacham (BLS) signature scheme:
BLS enables a very efficient aggregation of signatures but also allows reverse engineering of aggregated individual validator keys and is ideal for managing actions between validators.  
https://www.cryptologie.net/article/472/what-is-the-bls-signature-scheme/. 

# Validator Key:
same like others it exists in pair i.e public and private. 
purpose is to serve on chain operations like validation of block or propsoing or attesting.  
these keys are special and must be kept safe becausse it can disturp the whole chain. What if some thief got validator key of parrticipant who was actually a validator.  
- Being a proposer and can sign two different beacon blocks for the same slot. 
- Being an attester and signing an attestation that "surrounds" another one. 
- Being an attester and signing two different attestations having the same target. 


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
