# Tree
The core of the YouBase solution is the creation of a BIP32 hierarchical deterministic wallet tree for the control of access to personal data stores. The use of an wallet tree architecture offers the advantage of allowing for control of read/write access to individual leaves and branches of a tree. Additionally, this architecture allows for the designation of specific branches as data stores for specific types of information.

YouBase uses BIP39 12- (or more) word passphrases to seed a one-way hash function for the creation of a BIP32 hierarchical deterministic (HD) wallet tree.

The client software will manage the tree of Private-Public keys of the HD wallet, including a master key. Client software could exist on web (similar to CoinBase) on smartphone or on a local computer.

The HD contains a tree structure such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. 

At the first level, just under the Master Key, BIP43 suggests using only one branch, which will identify the purpose of the wallet. We propose using branch (x) to identify a data store. 

The next grandchild, or second layer below the master key layer will be designated as a profile layer. On this layer, we envision several types of profiles, including: an identity profile set, a health record profile, a financial profile, a social profile and more.

As a children to the health profile level, we there will be a collections layer. The collections layer will define many different types of health data collections. An immunization record could be considered.

To send an immunization record to a provider or a school district, the wallet owner could





