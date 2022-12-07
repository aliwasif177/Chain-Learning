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




# Deposit Data:





