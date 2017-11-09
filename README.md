# YouBase White Paper Summary (Draft 1.5)

By *Josh Robinson* & *Leonard Kish* & *Akhsar Kharebov*

## Entire Text: https://paper.youbase.io/content/index.html

### Abstract

YouBase enables individuals to create and maintain a personal data store on a distributed public network, allowing the unprecedented ability to easily gather, analyze, and share private data for any purpose imaginable. Data is structured hierarchically so that increasingly identifiable data can be placed at levels closer to the root, allowing arbitrarily anonymized data to be shared with whomever is requesting access to it.  The data format is flexible, enabling easy integration with third parties. In addition, read-only or read/write access can be granted at any node in the tree, allowing the user to tightly control access to every subtree in the data store. YouBase thus provides the building blocks for the ultimate peer-to-peer central repository for private data, enabling individuals, organizations, and the world to make smarter decisions.


### Introduction

Cryptography combined with distributed applications and databases in peer-to-peer networks provide the fundamental building blocks required for securing stores of individual-centered digital property in an open standards-based manner. By using encryption, digital signatures, digital wallets, and distributed data, ownership of digital information can be managed in a decentralized store. Such a store will be simultaneously secure and private, with strong identity services, while also available anywhere.

Information and rights to that information will ideally follow an individual as she moves through various contexts in her daily life, enabled with the ability to provide trusted, verified identity within those contexts. A longitudinal record could be created, including consumer-generated application data, with the individual as the primary controller of access - all independent of a third party.

YouBase provides an individual-centric security structure that separates personal data from identity while allowing for secure and structured read and/or write access to trusted parties on a peer-to-peer data store. This structure provides several benefits, including:

1. a way to securely input, access and share any kind of file or record
2. a way to organize authorized access to information into a structured hierarchy
3. improved anonymous information sharing that could be used as a public or shared private asset
4. information sharing transactions can be to be tied to financial transactions

With these tools in place, we imagine a world where, rather than storing personal data, third parties could simply subscribe to data owned and controlled by the individual.


### Implementation

YouBase introduces a new type of bitcoin HD wallet which uses BIP32 public-private key pair trees and couples this wallet with persistent peer-to-peer content-addressable key-value stores, such as IPFS. The new HD wallet implementation is responsible for maintaining the BIP32 nodes defining the hierarchical structure, metadata, and pointers to the actual data, as well as managing permissions and handling encryption/decryption.  We propose a distributed hash table for holding this BIP32 tree metadata as this makes it easier to access, backup, and sync. The peer-to-peer key-value store is treated as just that, a dumb key-value store, so technically it could be hosted locally, on the cloud, or on a peer-to-peer file system such as IPFS. Value would be maximized using IPFS as data would be public and decentralized.
