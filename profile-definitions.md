# Profile Definition

The profile definition is the blueprint for a profile. It defines what collections a profile contains, how to validate a collection's records, what to encrypt, and how to interact with the record.

At the top level, the profile definition only includes a title, type, and an array of collections. The type is used to group different types of related profile definitions together. Standards around the type field will be industry specific and defined separately with input from each industry.

```json
{
  "title": "Health Profile",
  "type": "health",
  "collections": [...]
}
```

## Collections

A profile's collections are defined as an array of collection objects, each having a title, type, schema, and form. A collection object's position in the array determines what branch it maps to under a profile. In a collection, the type field is used to describe the collections records in a consistent manner. This allows competing standards to create profiles that have a shared vocabulary. As with the profile type this will be industry specific and defined separately.

```json
{
  "title": "Health Profile",
  "type": "health",
  "collections": [{
      "title": "Allergies",
      "type": "allergy",
      "schema": {...},
      "form": [...]
  }, {
      "title": "Immunizations",
      "type": "immunization",
      "schema": {...},
      "form": [...]
  }]
}
```

### Schema

The schema field follows the [JSON Schema](http://json-schema.org) standard and is used to validate a record. The schema includes a title, JSON Schema type, properties, and list of required fields. The title is the singular name for a record as opposed to the plural name defined in the collection title. Unlike profiles and collections, the schema type must be defined as 'object' since we expect every record to be an object. This ensures the schema works with JSON Schema validators.

```json
{
  "title": "Health Profile",
  "type": "health",
  "collections": [{
    "title": "Allergies",
    "type": "allergy",
    "schema": {
      "type": "object",
      "title": "Allergy",
      "properties": {
        "allergen": {
          "title": "Allergen",
          "type": "string"
        },
        "description": {
          "title": "Description",
          "type": "string"
        }
      },
      "required": [ "allergen" ],
      "hardened": [ "allergen" ],
      "encrypted": [ "description" ]
    },
    "form": [...]
  }, {
    "title": "Immunizations",
    "type": "immunization",
    "schema": {...},
    "form": [...]
  }]
}
```

#### Properties

Following the JSON Schema standard, the properties field describes the properties of the record object.  Each property must be a JSON Schema primitive type.

#### Required

The required field, also part of the JSON Schema standard, is a simple array indicating to the validator which property keys must contain values.

#### Hardened

The hardened field is an extension to JSON Schema that is an array of property keys similar to the required field. Each property listed will be encrypted using the extended public key as the decryption key. This means the property will be unreadable by itself but can be decrypted when accessed as part of a tree.

As it is not possible to tell if a field is encrypted or just random data this is not checked by validators. Instead clients use the hardened field to know which properties it should expect are encrypted. It should also only reference properties that are of type 'string' instead of complex objects.

#### Encrypted

Properties listed in the encrypted field are similar to those in the hardened field but they are encrypted using the public key of the records node. This means they can only be decrypted by someone with the private key for that records node and limits access to someone with write access. Just as with the hardened field, encrypted properties cannot be validated and must be strings.  

### Form

A form definition is not required, but allows for hints to a client on how to generate a UI based only on the profile definition. This prevents the need for a custom client for every profile definition. The proposed format for defining forms comes from [Angular Schema Form](https://github.com/Textalk/angular-schema-form/blob/master/docs/index.md#form-definitions).

The proposed format includes some elements that are opinionated such as html class names that may not apply to every client. Because of this the form definition should only be used as a guide and not enforced or validated.

```json
{
  "title": "Health Profile",
  "type": "health",
  "collections": [{
    "title": "Allergies",
    "type": "allergy",
    "schema": {...},
    "form": [
      "allergen",
      {
        "key": "description",
        "type": "textarea",
        "placeholder": "Describe the allergy"
      },
      {
          "type": "submit",
          "style": "btn-info",
          "title": "OK"
      }
    ]
  }, {
    "title": "Immunizations",
    "type": "immunization",
    "schema": {...},
    "form": [...]
  }]
}
```
