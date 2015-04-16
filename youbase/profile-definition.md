# Profile Definition

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




