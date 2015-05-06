# Structured Data

The core of the YouBase solution is in a BIP32 hierarchical deterministic wallet or "HD Wallet" tree for the control of access to personal data stores.

The HD Wallet contains a tree structure with extended keys such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc. An extended key consists of a private or public key and a chain code. Sharing an extended key gives (private or public) access to the entire branch. A useful application is that a user can provide an extended private key to a trusted source that can then write (deposit) information in that tree without having read access to other information in the branch.

Providing public/private key pairings in such a structure offer a number of beneifts. First, information secured in wallets with the keys can follow a pre-specified structure where different kinds of information are stored in different branches of the tree.

Secondly, rights to different parts of the tree have permissions structured such that different parties can have different read/write permissions to single nodes or to entire branches. Specifically a private key is able to read/write data, a public key is only able to read data.

Finally, HD Wallets can create sequences of public keys without having access to the private keys, so that read-only or receive-only permission can be granted less secure environments without risking access to the private keys. From the outside (with access to a public key), there is no indication that the key is part of any larger structure. It becomes a bitcoin address like any other.

The use of an HD Wallet offers several advantages, including:

1. Allowing for control of read/write access to individual leaves and branches of a tree.

2. Partitioning data in separate branches allows users to grant access on a granular level.

3. The ability to designate specific branches as data stores for specific types of information.

4. The ability to tie payments to trusted information exchange.

5. Loss of key means only losing information for that part of the tree, which can be quickly marked as "dead" and copied to another address.

6. Rapid transfer of just about any type of data from one a party to another, a universal, secure email.

## Creating the wallet

HD wallets are created from a root seed, meaning they can be backed up, restored, exported and imported by transferring the root seed. Seeds can be stored through a mneumonic code so they are easy to transcribe and remember via BIP39.

The client software will manage the HD Wallet, including the encrypted seed and top-level master key pair. This client software could exist on the web, smartphone or on a local computer. Depending on where the client lives wallet access can be grantied via pin code, biometrics, or other means.

## Path levels

YouBase follows the recommendations in BIP43 and defines the following levels in a BIP32 path:

```
  m / purpose' / profile' / collection / record
```

The path follows standard BIP32 notation where 'm' represents the master node and an apostrophe indicates a hardened node. An example tree might look like the following with a detailed explanation of each level following.

```mermaid
{% include "diagrams/structured-data.md" %}
```

### purpose'

BIP43 recommends the use of a hardended purpose code to indicate the specification used by that subtree. We propose using branch 42' to identify a personal data store. All nodes under the specified purpose code should conform to the YouBase standard and will indicate to wallet software what to expect.

### profile'

The profile level is also hardened and is used to define the structure of the nodes under it. Each profile record points to a Profile Definition which the client uses to build the interface and interpret meaning of records. Profile Definitions are covered in detail in the next chapter. Some example profiles would be a health profile, identity profile, and social profile.

A YouBase wallet can have multiple profiles of the same type. A person may have multiple social profiles for example, one for each social group they are a part of. This allows you to grant different levels of access to different people depending on the context you define. Since each profile is hardened and on an isolated branch of the tree there is no way to know they are related without the owner of the profiles permission.

Although stored and accessed completely separately the client software may group together, or combine, related profiles. This will only be visible to the owner of the profiles and should only be done when it improves the users experience.

### collection

Collections are specified in the Profile Definition of the collections parent node (profile) and are used to hold groups of similiar records. In the previous diagram we used a health profile which defines an allergies collection and an immunizations collection. Since new profile types can be easily created the collections are not limited to any one standard.

### record

The record is the base unit of storage in YouBase. The format of these records is als specified in the Profile Definition and are defined using [JSON Schema](http://json-schema.org). This allows clients and other services with a way to read and validate a record without restricting profiles to using a single format.

In the current centralized world each service will often store user information in slightly different ways. By creating a Profile Definition that matches an existing service we can ease integration with it while giving YouBase clients a way to understand the information.
