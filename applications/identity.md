## Segregating Identy from Personal Information in Profiles (Could move to identity application)

The next grandchild, or second layer below the master key layer will be designated as a profile layer. This is a hardened key layer meaning that children cannot be derived from the parent’s public key to protect profiles information from inadvertent loss of private keys. 

Keys on this layer will represent repositories for various profiles defined in JSON. We recommend that a version of the JSON profile version be designated as the 0th child of the profile. On  the profile layer there could exist several types of profiles data sets, including: an identity profile set, a health record profile set, a financial profile, a social profile, application profile.

We’ll address greater detail in the “uses” section on Identity, but the identity profile branch could include identity profile information with multiple signed identity documents as evidence that keys are attached to these identifiers, verifiable to the same public keys. One could, for example, create hashes of identity documents. An individual could do a hash of identity profile and have an authorized person, such as a nurse in a physician’s office, digitally sign it, saying that this person belongs to this profile.  One could hash of an image of an individual’s driver’s license, for instance that was signed by an authority as valid, much like a Notary verifies identity and signatures today on paper. 

The process irrevocably ties the signature (the signer) to digital property asset stores in other areas of the tree, verifying an identity without revealing it. The HD structure enables an internal mathematical consistency for quick verification at the user level to prove an individual's data is valid for them, but no way to relate two public keys as being related without such key access. An advantage of this system is that whether an individual is tied to a certain piece of information is quickly provable without releasing personal information. 

Use case example:
I have a piece of identification unique to me, say a picture of a driver’s license or an insurance card. I can send an encrypted message that's encrypted with the recipient’s public key. Only they can decrypt it as only they have the private key. It could be signed by another’s entities private key in a transaction, and therefore verifiable with a public key.

So, using public and private key signature schemes, only those with the private key for a public key with which a message is hashed will be able to receive the information, much like the recipient of a locked box. Based on public and private key pairs, we can therefore ensure the identity of someone sending information, without publicly declaring who that person is with personal information.  The payload within the locked box can confirm their information.

This scheme alleviates many problems with many current identity and security mechanisms, which rely on personal information to confirm identity, and are therefore the focus of attacks. It also segregates identity information from other personal information, such that this personal information can be repurposed without revealing identity information, say, for public health benefits. We'll discuss other such use cases in the "applications" section.

