# Tree

YouBase will use BIP39 12- (or more) word passphrase to seed a one-way hash function to create a BIP32 hierarchical deterministic (HD) wallet tree. 

The client software will manage the tree of Private-Public keys of the HD wallet, including a master key. Client software could exist on web (similar to CoinBase) on smartphone or on a local computer.

The HD contains a tree structure such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. 

At the first level, just under the Master Key, BIP43 suggests using only one branch, which will identify the purpose of the wallet. We propose using branch (x) to identify a data store. 

The next grandchild, or second layer below the master key layer will be designated as a profile layer. On this layer, we envision several types of profiles, including: an identity profile set, a health record profile, a financial profile, a social profile and more.

As a children to the health profile level, we there will be a collections layer. The collections layer will define many different types of health data collections. An immunization record could be considered.

Get into SCHEMA here.



