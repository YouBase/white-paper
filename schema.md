# Schema

Schemas will be defined via JSON. Below is an example of a sample health profile definition:

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




