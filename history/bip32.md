# BIP32

BIP0032, stands for Bitcoin Improvement Proposal or "bip32", is a bitcoin wallet standard for hierarchical deterministic or "HD wallets". Hierarchical deterministic wallets have tree structures where public/private parent keys can create a sequence of child keys, child keys can create a sequence of grandchild keys, and so on with an infinite number of generations and keys. Each parent can generate 2 billion children keys.

Providing public/private key pairings in such a structure offer a number of beneifts. First, information secured in wallets with the keys can follow a pre-specified structure where different kinds of information are stored in different branches of the tree. The structure of the bip32 tree itself can be specified in such a branch. For example, a company could have different branches for different departments and accounting categories, as an example, accepting payments.

Secondly, rights to different parts of the tree have permissions structured such that different parties can have different read/write, spending or depositing permissions to single nodes or to entire branches. 

Finally, HD wallets can create sequences of public keys without having access to the private keys, so that read-only or receive-only permission can be granted less secure environments without risking access to the private keys.

HD wallets are created from a root seed, meaning they can be backed up, restored, exported and imported by transferring the root seed. Seeds can be stored through a mneumonic code so they are easy to transcribe and remember via bip39.

Also, from the outside (with access to a public key), there is no indication that the key is part of any larger structure. It becomes a bitcoin address like any other. 

Another important facet however is that, through xxxx it can be verified that both keys came from a similar ancestor. So, if one branch of the key contained identity mechanisms, another could verify that the data came from someone with that identity.


