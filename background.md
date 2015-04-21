# Background

## BIP32

BIP0032, stands for Bitcoin Improvement Proposal or "bip32", is a bitcoin wallet standard for hierarchical deterministic or "HD wallets". Hierarchical deterministic wallets have tree structures where public/private parent keys can create a sequence of child keys, child keys can create a sequence of grandchild keys, and so on with an infinite number of generations and keys. Each parent can generate 2 billion children keys.

Providing public/private key pairings in such a structure offer a number of beneifts. First, information secured in wallets with the keys can follow a pre-specified structure where different kinds of information are stored in different branches of the tree. The structure of the bip32 tree itself can be specified in such a branch. For example, a company could have different branches for different departments and accounting categories, as an example, accepting payments.

Secondly, rights to different parts of the tree have permissions structured such that different parties can have different read/write, spending or depositing permissions to single nodes or to entire branches. 

Finally, HD wallets can create sequences of public keys without having access to the private keys, so that read-only or receive-only permission can be granted less secure environments without risking access to the private keys.

HD wallets are created from a root seed, meaning they can be backed up, restored, exported and imported by transferring the root seed. Seeds can be stored through a mneumonic code so they are easy to transcribe and remember via bip39.

Also, from the outside (with access to a public key), there is no indication that the key is part of any larger structure. It becomes a bitcoin address like any other. 

Another important facet however is that, through xxxx it can be verified that both keys came from a similar ancestor. So, if one branch of the key contained identity mechanisms, another could verify that the data came from someone with that identity.

## Bitcoin

Bitcoin started in early 2009 with a white paper and reference implentation by an unknown entity or entities referring to themself(ves) as Satoshi Nakamoto. Records of payments using the virtual currency are stored in a public leger that is agreed upon and stored on bitcoin users' computers. The ledger, known as the blockchain, in combination with crytopgraphy and the bitcoin protocol, solve what's known as the "double spending" problem by achieving consensus throughout the network on what coins have been spent where. 
Consensus is validated by a process called "proof of work". Blockchain and proof of work are the key breakthroughs that has allowed bitcoin to rapidly become widely adopted, with approximately $10 billion in circulation, with no central authority.

Bitcoin and the blockchain can also be seen as a generalized accounting system that can be used for tracking many types of transactions and assets beyond just cryptocurrency. Transaction and accounting could include voting, notarization and identity, lotteries, asset registries, and the exchange of tangible and intangible (e.g. data) assets. Digital identity through public-private cryptographic keying and digital signatures could be used to manage read and write access to a wide variety of data stores, for example, activation of certain assets, or entry into real world properties. Assets can be registered to the blockchain in a tranaction that includes access methods, priveledges and a pointer to off-chain files.

## DHT

Distributed Hash tables are a decentralized, distributed system for storing key/value pairs where any node in the network can efficiently retrieve a value given a certain key. Ability to map keys to values is distributed among the nodes, such that changes to participating nodes is minimally disruptive.

From Wikipedia: 

"The structure of a DHT can be decomposed into several main components.[8][9] The foundation is an abstract **keyspace**, such as the set of 160-bit strings. A **keyspace partitioning scheme** splits ownership of this keyspace among the participating nodes. **An overlay network** then connects the nodes, allowing them to find the owner of any given key in the keyspace.

Once these components are in place, a typical use of the DHT for storage and retrieval might proceed as follows. Suppose the keyspace is the set of 160-bit strings. To store a file with given filename and data in the DHT, the SHA-1 hash of filename is generated, producing a 160-bit key k, and a message put (k, data) is sent to any node participating in the DHT. The message is forwarded from node to node through the overlay network until it reaches the single node responsible for key k as specified by the keyspace partitioning. That node then stores the key and the data. Any other client can then retrieve the contents of the file by again hashing filename to produce k and asking any DHT node to find the data associated with k with a message get(k). The message will again be routed through the overlay to the node responsible for k, which will reply with the stored data."

## IPFS

IPFS, or Interplanetary Proprietary File System, is completely peer to peer file system with files encrypted and versioned. File-sharing network nodes are rewarded with filecoin for their work in storing and serving. Due to P2P nature, IPFS is unified and permanently accessible file system that is independent of any single entity or central repository.

## TOR

TOR, or, as it was initially called, The Onion Router, is free and open source software for anonymous communication that works by progressively encrypting and decrypting messages, including the destination address, as messages move through network nodes. 
