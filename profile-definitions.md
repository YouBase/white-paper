# Profile Definition

The profile definition is the blueprint for a profile. It defines what collections a profile contains, how to validate a collections records, what to encrypt, and how to interact with the record.

At the top level the profile definition only includes a title, type, and an array of collections. The type is used do group different types of related profile definitions together. Standards around the type field will be industry specific and defined separately with input from each industry.

```json
{
  "title": "Health Profile",
  "type": "health",
  "collections": [...]
}
```

## Collections

Collections are defined as an array of collection objects with a title, type, schema, and form. A collection objects position in the array determines what branch it maps to under a profile. In a collection the type field is used to describe the collections records in a consistent maner. This allows competing standards to create profiles that have a shared vocabulary. As with the profile type this will be very industry specific and will be defined separately.

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

The schema field follows the [JSON Schema](http://json-schema.org) standard and is used to validate a record. It includes a title, JSON Schema type, properties, and list of required fields. The title is the singular name for a record as apposed to the plural name defined in the collection title. Unlike the profile and collection levels in the schema a type must be 'object' since we expect every record to be an object. This makes the sure the schema works with JSON Schema validators.

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

Following the JSON Schema standard the properties field describes the properties of the record object and the type must be a JSON Schema primitive type.

#### Required

The required field is also part of the JSON Schema standard and tells the validator what properties must contain values. It is a simple array of the property keys that are required.

#### Hardened

The hardened field is an extention to JSON Schema that is an array of property keys similiar to the required field. Each property listed will be encrypted using the extened public key as the decryption key. This means the property will be unreadable by itself but can be decrypted when accessed as part of a tree.

Since it is not possible to tell if a field is encrypted or just random data this is not checked by validators. Instead clients use the hardened field to know which properties it should expect to be encrypted. It should also only reference properties that are of type 'string' instead of complex objects.

#### Encrypted

Properties listed in the encrypted field are similiar to those in the hardened field but they are encrypted using the public key of the records node. This means they can only be decrypted by someone with the private key for that records node and limits access to someone with write access. Just like the hardened field encrypted properties can not be validated and must be strings.  

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
