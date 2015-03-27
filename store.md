# Store

Referring to the UnPatients model implementation of YouBase.

Sensitive document storage, such as in healthcare, today relies on both trust and confidence in 3rd parties. Unfortunately, the many recent healthcare data breaches have shown that data stored in this way is not safe. Furthermore, data not subject to hacking may nevertheless be released voluntarily when ownership of the entity housing that data changes hands, as in the recent case with Radio Shack. YouBase solves this problem by deploying a combination of two of the most important themes in computing - cryptographic hashing and distributed peer-to-peer networks - to store, manage, transfer and share data. 

YouBase will you use the IPFS distributed hash table (DHT). We can think of IPFS as bringing together the best ideas from other DHTs, as well as from BitTorrent, Github and self-certifying file systems. 

Unlike in the Skype or BitTorent networks where every client is also a server, YouBase allows but does not require clients to also act as servers (of the distributed hash table). Instead YouBase, and specifically in its UnPatients implementation, utilizes the existence of large, non-cooperative, regulated entities (insurance companies, healthcare providers, and others) to serve the distributed hash table. 

YouBase brings together the best of the free net (Gnutella, Torrent, etc.) with the best of ideas from server-based file sharing (Napster) and leverages the existence of particular legal/regulatory regimes (in the case of our model implementation, healthcare, rules related to privacy, data storage, and competition). By leveraging these rules, YouBase allows users to act as a data node should they choose, but does not require it. This allows us to build lightweight clients and makes sure the data is stored on several servers that are more permanent. 

These servers will be owned and run by existing organizations within the highly regulated healthcare ecosystem. These organizations are legally and ethically prevented from engaging in privacy-jeopardizing collusion. We refer to them as "non cooperative entities" ("NCE"s) and they may include payers (insurance companies, governments), in-vitro diagnostic labs, patient advocates, and non-profit groups. These non-cooperative entities will run servers and each server will contain part of the DHT. 

[This will also add to efficiency, as a limited amount of work will need to be done because similar nodes will interact frequently]

Further, the next version of the model YouBase implementation contemplates an even greater level of storage security which we refer to as:  Mutually Assured Privacy (for v2 of the UnPatients manifesto). In this advanced version, the recipient of the information (the doctor or medical AI) is putting his/its own private key on the line. Under the Mutually Assured Privacy system "uou have to protect your information as if it was your own, because it is"

