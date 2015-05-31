# Structured Data

The core of the YouBase solution is a new kind of BIP32 hierarchical deterministic wallet or "HD Wallet" tree for the control of access to personal data stores.  YouBase's wallet implementation follows the recommendations in BIP43 for extending BIP32, and can thus be thought of as BIP46, following the examples set in BIP44 and BIP45.

The HD Wallet contains a tree structure with extended keys such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. An extended key consists of a private or public key and a chain code.  Sharing an extended key gives (private or public) access to the entire branch. A useful application is that a user can provide an extended private key to a trusted source that can then write (deposit) information in that branch of the tree without having access to information in other branches.

Providing public/private key pairings in such a structure offers a number of benefits. First, specific branches can be used as data stores for specific types of information. Information secured in wallets can follow a pre-specified structure where different kinds of information are stored in different branches of the tree. 

Secondly, along with that data structure, different rights to the tree have permissions structured such that different parties can have different read/write permissions to single nodes or to entire branches. Data can be partitioned into separate branches, allowing users to grant access on a granular level, down to the individual record, or even changes to a record. Specifically, a private key has read/write access to the data while a public key has read access only.

Third, HD Wallets are flexible in that they can create sequences of public keys without having access to the private keys, so that read-only or receive-only permission can be granted in less secure environments without risking access to the private keys. From the outside (with access to a public key), there is no indication that the key is part of any larger structure. It becomes a bitcoin address like any other.

In additon, 
3. Tie payments to trusted information exchange.

4. Quickly and easily recover from data breaches. Since a compromised key means only information in that part of the tree is compromised, such keys can be quickly marked as "dead" and all associated data can be copied to another address.

5. Rapidly transfer just about any type of data from one a party to another. Think of a universal, secure email for data with unique addresses that are verifiable, but private.

## Creating the wallet

HD wallets are created from a root seed, meaning they can be backed up, restored, exported and imported by transferring the root seed. Seeds can be stored through a mnemonic code so they are easy to transcribe and remember via BIP39.

The client software will manage the HD Wallet, including the encrypted seed and top-level master key pair. This client software could exist on the web, smartphone or local computer. Depending on where the client lives, wallet access can be granted via pin code, biometrics, or other means.


## Path levels

YouBase follows the recommendations in BIP43 and defines the following levels in a BIP32 path:

```
  m / purpose' / profile' / collection / record
```

The path follows standard BIP32 notation where 'm' represents the master node and an apostrophe indicates a hardened node. An example tree is illustrated in the following diagram:

![Structured Data](/diagrams/structured-data.png)

### purpose'

BIP43 recommends the use of a hardened purpose code to indicate the specification used by that sub-tree. We propose using branch 46' to identify a personal data store. All nodes under the specified purpose code should conform to the YouBase standard and will indicate to wallet software what to expect.

### profile'

The profile level is also hardened and is used to define the structure of the nodes under it. Profile nodes point to a profile definition which the client uses to build the interface and interpret meaning of collections and records. Profile definitions are covered in detail in the next chapter. Profiles can be any set of interrelated data like health, identity, or social media.

A YouBase wallet can have multiple profiles of the same type. A person may have multiple social profiles for example, one for each social group they are a part of. This allows you to grant different levels of access to different people depending on the context you define. Since each profile is hardened and on an isolated branch of the tree there is no way to know they are related without the owner of the profile's permission.

Although stored and accessed completely separately the client software may group together, or combine, related profiles. This will only be visible to the owner of the profiles and should only be done when it improves the user's experience.

### collection

Collections are specified in the profile definition of the collection's parent node (profile) and are used to hold groups of similar records. In the previous diagram we used a health profile which defines an allergies collection and an immunization collection. Since new profile types can be easily created the collections are not limited to any one standard.

### record

The record is the base unit of storage in YouBase. The format of these records is also specified in the profile definition and is defined using [JSON Schema](http://json-schema.org), a standard for describing easily validated JSON data formats.  Using this standard, profiles are not restricted to using a single format, providing the flexibility necessary to implement any conceivable application. In today's centralized world, each service has its own rigid, mutually incompatible data format. YouBase's JSON schema enables the creation of a profile definition that matches any existing format, easing the integration process while also helping clients understand the data by presenting it in a familiar way.
