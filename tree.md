# Tree

BIP 39 allows for a 12 word-passphrase to seed the tree structure that BIP32 will create via a one-way hash function to create a hierarchical deterministic wallet, or HD. The client software will manage the tree of Private-Public keys of the HD wallet, including a master key. Client software could exist on web (similar to CoinBase) on smartphone, in the cloud or on a local computer.

The HD contains a tree structure such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. 

At the first level, just under the Master Key, bip43 suggests using only one branch, which will identify the purpose of the wallet. We propose using branch (x) to identify a data store. 

The next grandchild, or second layer below the master key layer will be designated as a profile layer. On this layer, we envision several types of profiles, including: an identity profile set, a health record profile, a financial layer, an online identity layer for social accounts and more.



