# Distributed Storage

By using an HD Wallet to hold the structure of the data, it's storage is simplified. Every node in the tree is stored as a JSON document in a document store where the lookup key is the node's address derived from it's public key. Storing documents in this way provides flexibility and allows a user to keep YouBase documents in a local filesystem, cloud storage, or our proposed distributed system. At the same time it allows a user to easily sync documents between different storage systems.

In YouBase the distributed storage is made of three main components, the BIP32 Node being stored, a signed JSON document, and storage for linked data. The following diagram illustrates how each interacts with the other.  

![Distributed Storage](/diagrams/distributed-storage.png)

## BIP-32 Node

Data can be stored at every node in the HD Wallet tree by creating a signed JSON Document. The public and private keys are not stored in the document but are used to secure the document and control access to it. Large amounts of data can be stored at the node by using the link storage, described later.

## Document

The document is stored in a DHT where the lookup key is an address generated from the public key. The document is saved as JSON and contains the address as an id, revision, document data, document links, and a signature.

```json
{
    "_id": "address generated from public key",
    "_rev": "hash of data + links + _lastrev",
    "_lastrev": "points to previous _rev if this document is an update",
    "data": {...},
    "links": [...],
    "notaries": {...},
    "signature": "signature of _rev"
}
```

### ID - Address

The document's id is an address generated from the public key and is a valid bitcoin address. It is used as the lookup key but also included in the saved document to make syncing and validating easier.

### Data

The data field is the core of a document. It contains timestamps, references to profile definition, issuer, signatures, demographic information, and the actual information to be stored. The data field follows a standard format defined in a separate YouBase specification document. The data field can also reference links as described in the next section.

```json
{
    "_id": "address generated from public key",
    "_rev": "hash of data + links + _lastrev",
    "_lastrev": "points to previous _rev if this document is an update",
    "data": {
        "type": "record",
        "profile": "hash of profile definition",
        "issuer": "address of entity creating the record",
        "timestamp": "2015-05-21T20:21:46.612Z",
        "demographics": {
            "geohash": "9xj",
            "gender": "female",
            "age": 24
        },
        "record": {...} // record data as defined in the profile definition
    },
    "links": [...],
    "notaries": {...},
    "signature": "signature of _rev"
}
```

### Links

Documents as defined above should be kept small in order to be transferred in a fast and efficient manner. To handle larger records and attachments, YouBase uses a links field containing references to a content addressable data store (such as IPFS). The links field is an array of link objects similar to the format used in IPFS. 

```json
{
    "_id": "address generated from public key",
    "_rev": "hash of data + links + _lastrev",
    "_lastrev": "points to previous _rev if this document is an update",
    "data": {...},
    "links": [
        {
            "name": "arm-xray.png",
            "hash": "hash of arm-xray.png contents",
            "size": 12345678
        },
        {
            "name": "leg-xray.png",
            "hash": "hash of leg-png.png contents",
            "size": 12345678
        }
    ],
    "notaries": {...},
    "signature": "signature of _rev"
}
```

Each link object will have a name, size, and hash. The hash is a hash of the referenced content. This allows for using the content hash as a lookup key to the data store. Using this strategy drives efficiency as multiple files with the same content have the same lookup key, preventing the storage and retrieval of the same content multiple times. There's an added benefit of validating the content returned by hashing it and making sure the hash matches the key.

### Revision - Document Hash

A revision is similar to a revision in CouchDB. In YouBase, however, the revision is always a hash of the data and link field. Any updates to a node need to reference the document revision they are updating as "\_lastrev" which is included in the hash creating "\_rev".

YouBase will return the most recent revision of any document unless a specific revision is requested. Revisions should be kept to allow viewing of the entire history of a node's data.

### Notaries

Notaries are entities that are not the wallet owner but certify the validity of the data. As notaries are not included in the document hash (\_rev), they can be added to and removed at will without changing the validity of a document. 

The only required signature in the notary field is that of the issuer. If an issuer is listed in the data field of the document, the issuer should also have a valid signature in the notaries list. With the exception of the issuer signature, if the notary field contains an invalid signature then it should simply be removed instead of invalidating the entire document. 

```json
{
    "_id": "address generated from public key",
    "_rev": "hash of data + links + _lastrev",
    "_lastrev": "points to previous _rev if this document is an update",
    "data": {...},
    "links": [...],
    "notaries": {
        "bitcoin address of notary": "signature of _rev"
    },
    "signature": "signature of _rev"
}
```

### Signature

To ensure a document is valid it must include a signature of the document hash by the node's private key. When a document is saved the document store simply checks the signature against the document hash and id.

## Link Storage - Content Addressable Data Store

As mentioned above, the link storage is a key value store where the lookup key is a hash of the contents. This can be as simple as a file saved to the local file system, where the file name is a hash of the file content or a proprietary cloud solutions like Amazon S3 where, again, the file name is a hash of the contents. IPFS is the logical choice for YouBase at this time as IPFS fulfills current requirements for a distributed store, independent of any one 3rd party.
