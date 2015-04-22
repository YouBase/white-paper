# Profile Definition

The collection layer of keys under a profile will define a schema. Schemas will be defined via JSON. Below is an example of a sample health profile definition:

```json
{
    "title": "Health Profile",
    "type": "health",
    "collections": [{
        "title": "Allergies",
        "type": "allergy",
        // [JSON Schema](http://json-schema.org)
        "schema": {
            "type": "object",
            "title": "Allergy",
            "properties": {
                "allergen": {
                    "title": "Allergen",
                    "type": "string"
                }
            },
            "required": [
                "allergen"
            ]
        },
        "form": [
            "allergen",
            {
                "type": "submit",
                "style": "btn-info",
                "title": "OK"
            }
        ]
    }
  ]
}
```

meta: timestamp
attachments, files, sample time, steps or could be in a file. 

Client sends JSON message in a consistent way, we verify the hashes, we create the record. 

Payload will be hashes pointing to IPFS. 

Profile definition will specify what things in the payload and attachments to encrypt. Payload will be in the format of JSON with keys and values.

Default metadata: timestamp, demographic def, age at time of record, geohash. Would be configurable on the client.

Client, sends to IPFS, IPFS could be hashed. IPFS gives lookup key to the data.

ID with JSON, signature of a hash of the JSON. DHT uses bitcoin address (derived from public key) as the lookup, with JSON will include public key, signature of 


