# YouBase Tree
The core of the YouBase solution is in a BIP32 hierarchical deterministic wallet tree for the control of access to personal data stores. The use of an HD wallet offers several advantages, including:  1) allowing for control of read/write access to individual leaves and branches of a tree, 2) segregating identity profile information from other profile information, so information is trusted without relying on personal data, 3) the ability to designate specific branches as data stores for specific types of information and, therefore, the use of specific branches identify the purpose of the tree  4) the ability to tie payments to trusted information exchange. 

## Seeding and creating the HD Wallet


YouBase uses a BIP32 hierarchical deterministic wallet (or "HD Wallet") which is seeded through a BIP39 12 or more word passphrase. The passphrase seeds a hash function for the creation of a BIP32 hierarchical deterministic (HD) wallet tree. It’s a flat key structure that is reconstituted in the Wallet. 
Structured read write access control can then be avaialbe with the use of keys.

The client software will manage the tree of Private-Public keys of the HD wallet, including a top-level master key. This client software could exist on web (similar to CoinBase),  smartphone or on a local computer. Verifications to access nodes in the tree could be combined with biometric scans on a local device such as a smartphone.

## Structure

(Insert graphic here)

The HDWallet contains a tree structure such that each parent key can derive the children keys, children keys can derive the grandchildren keys, etc.  

At the first public/private key level of the hierarchy, just under the Master Key, BIP43 suggests using only one branch which will identify the purpose of the wallet. We propose using branch 42 to identify a personal data store. 

Segregating Identification from Personal Information in Profiles

The next grandchild, or second layer below the master key layer will be designated as a profile layer. This is a hardened key layer meaning that children cannot be derived from the parent’s public key to protect profiles from inadvertent loss of private keys. 

Keys on this layer will represent repositories for various profiles defined by JSON. We recommend that a version of the JSON profile be designated as the 0th child of the profile. On  the profile layer there could exist several types of profiles data sets, including: an identity profile set, a health record profile set, a financial profile, a social profile, application profile.

We’ll address greater detail in the “uses” section on Identity, but the identity profile branch could include identity profile information with multiple signed identity documents as evidence that keys are attached to these identifiers, verifiable to the same public keys. One could, for example, create hashes of identity documents. An individual could do a hash of identity profile and have an authorized person, such as a nurse in a physician’s office, digitally sign it, saying that this person belongs to this profile.  One could hash of an image of an individual’s driver’s license, for instance that was signed by an authority as valid, much like a Notrary verifies identity and signatures today on paper. 

The process irrevocably ties the signature (the signer) to digital property asset stores in other areas of the tree, verifying an identity without revealing it. The HD structure enables an internal mathemantical consistency for quick verification, but no way to relate two public keys as being related. An advantage of this system is that whether an individual is who they say they are become a verifiable binary (yes/no) piece of information rather than a store of personal information. 

Use case example:
I have a piece of identification unique to me, say a picture of a driver’s license or an insurance card. I can send an encrypted message that's encrypted with the recipient’s public key. Only they can decrypt it as only they have the private key. It could be signed by another’s entities private key in a transaction, and therefore verifiable with a public key.

So, using public and private key signature schemes, only those with the private key for a public key with which a message is hashed will be able to receive the information, much like the recipient of a locked box. Based on public and private key pairs, we can therefore ensure the identity of someone sending information, without publicly declaring who that person is with personal information.  The payload within the locked box can confirm their information.

This scheme alleviates many problems with many current identity and security mechanisms, which rely on personal information to confirm identity, and are therefore the focus of attacks. It also segregates identity information from other personal information, such that this personal information can be repurposed without revealing identity information, say, for public health benefits.

## Collections


As a children to the health profile level, part of the health branch we there will be a collections layer. The collections layer will define many different types of health data collections. An immunization record, a list of allergies, current and past medications could all be included as various collections.

Our health collections are based on FHIR Resource Index, available here: http://www.hl7.org/implement/standards/fhir/resourcelist.html




