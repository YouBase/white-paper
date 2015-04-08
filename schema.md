# Schema

[This is where we take some existing healthcare lab report or EMR/EHR code schema(s) and map them to elements that we can efficiently hash and store, per the prior section ("Store")]

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




