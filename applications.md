# Applications

YouBase is designed to provide a substrate on which any individual-centric service can be built. Instead of defining all possible application we are providing several potential use cases and examples on how YouBase can be used to solve specific problems. We intend to follow with industry-specific papers on how YouBase can be used to solve a wide variety of personal data store problems.

## Identity

By default, YouBase does not contain or require any personally-identifiable information.  However for uses such as logging into a site or providing government-issued identification, an identity profile can be defined. Keeping all identity information in an identity profile keeps it siloed from all other personal information with an individual's YouBase wallet. An individual would be able to create multiple identity profiles to separate data even further and provide fine-grain control.

An identity profile could have a collection dedicated to government issued IDs giving the authorizing entity write access to that collection. This would allow the authorizing entity to write ids directly to a person's wallet including an issuer signature to prove the ID is valid. By owning the private key to that profile, a person could verify that the ID is both valid and owned by them.

Logging into a service with an ID simply requires signing a message with the profile's private key that can then be validated with the public key. This allows for authentication without transferring sensitive information.

## Social Networks

Using a method similiar to [Keybase](https://keybase.io) and [Onename](https://onename.com) an identity profile can be linked to existing social network accounts (twitter, facebook, github, etc.) by publicly posting a message signed with the private key of a profile. The message can then be used to prove the owner of a specific identity profile is in control of that social network account.

A social profile could contain collections of posts, blog articles, pictures, and other information we want to share with different groups. By having a separate social profile for each social group, a person would be able to keep their work life separate from their online personal life, for example.  

As each node in a profile is a fully functional bitcoin addresss, bitcoin can be sent to any record, collection, or profile. "Like" buttons can be replaced with "tip" buttons that go directly to supporting the content creator. Care would need to be taken when transferring funds to another bitcoin address to prevent re-association of data in private data contexts, but wouldn't be an issue for public content.

Attachments are stored in a content-addressable data store. This means that when someone shares the same content as another person, it points to the file already in the data store instead of uploading a new file. This happens any time the content is the same, even if two people upload the same file separately.

With each person owning their data instead of the social network owning it, users would be able to take the same profile and make it available for use on multiple social networks. They would be able to tryout the latest service without having to start from scratch and lose their entire history.

## Healthcare

There are a number of widely-known problems in health IT that an individual-centric data store could help solve.

**Security** Breaches in health care have become all-too-common because of the high value to identity thieves. A premium is paid on the black market for such records, estimated at $50 per record. In the US Q1 2015 alone, nearly 90 million medical records have been compromised, including identity, clinical and financial information. At least part of the problem is misaligned incentives between third parties and patients. Providing a repository of data independent of a 3rd party could provide a framework where personal data is provided on a subscription basis, rather than stored in multiple locations by multiple 3rd parties.

**Access**. At the same time, a person's ability to access and manage personal information currently resting with third parties is difficult, recently leading to the #NoMUWithoutME and getmyhealthdata.org campaigns for personal health information access. Ideally, each person will have a private, universal and secure container that belongs to the individual or patient and serves as reference for health care stakeholders.

**Interoperability**. YouBase is data agnostic and could act as a single source for data, shared as needed and controlled by the patient, independent of data types. Data within the store could be translated between the various profiles. Any kind of data profile can be accepted and defined in the schema, there's no need to pre-define the data structure before receiving the payload.

**Research**. Consumers can anonymously donate their *validated* data with minimal metadata or personal information. Consumers can have a personal container to directly connect their validated clinical and claims data, or provide this validated information to an external party.

**Identification at point of care**. YouBase can provide validated identity at the point of care through IDs, unique addresses and digital signatures, while maintaining privacy. Digital signatures will improve data quality.

**Sending records from provider to patient**. A set of universal addresses will allow for secure transmission of a patient record, simply by scanning an public address for which the health care provider has a private key.

These are just a few examples. Our goal here is not to identify every use for the YouBase platform, only to provide a starting point to consider a new way for managing health information around trusted identity and privacy.

Use case:

Using digital signatures, YouBase will allow for each participant in a health care transaction to have a YouBase store that will allow each to verify their identity, have the identity signed as valid, then attach a health measurement or record to that identity.  YouBase wallets would act to validate an identity, and the keys would server as both a unique ID and a data address.

For example, a user would enter a lab, show that his identity matches with a traditional ID or, simply present his YouBase token that has been signed. The public key token is then verified as belonging to the user and documented in the system. The phlebotomist takes a blood sample, notes the date/time, and the sample is then permanently associated with the user's token/private-key. The sample is processed using the lab's existing system. The results (data) are sent to user's YouBase wallet and can only be opened/viewed by the token/secure-key.

This could be applied to many health care transactions, creating validated identity and a universal set of addresses to which patient information could be signed. Using this kind of a system we expect will also improve data quality as each data entry will require a digital signature linked to the person who entered the information.



