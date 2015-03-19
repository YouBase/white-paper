# Tree

BIP 39 allows for a 12 word-passphrase to seed the tree structure that BIP32 will create via a one-way hash function to create a hierarchical deterministic wallet, or HDN. The client software will manage the tree of Private-Public keys, including a master key. Client software could exist on web (similar to CoinBase) on smartphone, in the cloud or on a local computer.

The HDN contains a tree structure such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. 



