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


# Day 4:


# EIPI Typed Transaction Enevelope:
contain two main payload in transaction.  
- Transaction type ( a number btw 0 to 0*7f for total 128 typess of transactions). 
- Transaction payload ( arbitrary byte array of data based on selected transaction type btw 0 - 0*7f). 

# Block:
Blocks are bactches of transaction. when there are limited number of trabnsaction occurs on network. network make a collection/bactch of these transactions and constitute a block.  
In chain all blocks are linked togather by keeping the hash of prevoius block and then produce combine hash of previous block own data and then pass this hash address to next block. 
So in this way if one block data chhanges its hash will change and subsequently all blocks in chain will invalidate this change.    


# Day 5:

# Nodes:
Machines that are running on Ethereum network that are responsible for verifying blocks and transactions and it coukd be attester, validator or proposer. These machines can be miner and other machines that participate in keeping network. But after merge a node cannot execure on its own. It needs consensus client ( which staked coin ) to work with.  

# Execution client:
Refers to the nodes that were involved in POW in eth1 responsible for keeping track of new transactions updating database and evm state by connecting and aggregation to all other nodes acroos network.  

# Consensus client:
Refers to client/node which have stacked chain coins in order to propose the block/transaction passed on from execution client.  

# Day 6:

# Block time:
In network when lrage number of transactions bundled up then it is time to make blocks and seperate them and then link to chain. So for tis validator needs to propose a block. In network after every 12 seconds they proposes a block and these 12 seconds are called slot. Sometime max nodes/machines might be offline and network can let go that slot empty because it corresponds to that offline validator.

# Block size:
Each block in network chain has a limited size of 15 million gas. But It can be expand or shrink based on requirments. At max block can hold transaction of 30 million gas (2x of initial limit). Accumulative gas of transactions should always be less than the limit.  
If we have a block size of more than 30 million it will have extra large size then it will be difficult to validate this for low performant node and thus time taking and require more power consuption.  













