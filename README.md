
## Ejercicio JSON Schema

[Enlace](https://www.liquid-technologies.com/online-json-schema-validator) al **validador** usado

**Soluciones**

- Ejercicio 1 (schema -> json) : [Fichero](/ejercicio1/json.json)
- Ejercicio 2 (json -> schema) : [Fichero](/ejercicio2/schema.json)

### Enunciados

1. Crea un **JSON** que sea válido con el [siguiente JSON Schema](/ejercicio1/schema.json):

```json
{
    "$schema": "https://json-schema.org/draft/2020-12/schema#",
    "$id": "http://example.com/schemas/painting.schema.json",
    "type": "object",
    "title": "Painting",
    "description": "Painting information",
    "required": ["name", "artist", "dimension", "description", "tags"],
    "properties": {
        "name": {
            "type": "string",
            "description": "Painting name"
        },
        "artist": {
            "type": "string",
            "maxLength": 50,
            "description": "Name of the artist"
        },
        "description": {
            "type": ["string", "null"],
            "description": "Painting description"
        },
        "dimension": { "$ref": "#/$defs/dimension" },
        "tags": {
            "type": "array",
            "items": { "$ref": "#/$defs/tag" }
        }
    },
    "$defs": {
        "tag": {
            "type": "string",
            "enum": ["oil", "watercolor", "digital", "famous"]
        },
        "dimension": {
            "type": "object",
            "title": "Painting dimension",
            "description": "Describes the dimension of a painting in cm",
            "required": ["width", "height"],
            "properties": {
                "width": { "type": "number", "description": "Width of the product",
                "minimum": 1 },
                "height": {
                    "type": "number", "description": "Height of the product",
                    "minimum": 1
                }
            }
        }
    }
}
```


2. Crea un **JSON Schema** que sea válido para el [siguiente JSON](/ejercicio2/json.json):

```
{
    "squadName": "Super hero squad",
    "homeTown": "Metro City",
    "formed": 2016,
    "secretBase": "Super tower",
    "active": true,
    "members": [
        {
            "name": "Molecule Man",
            "age": 29,
            "secretIdentity": "Dan Jukes",
            "powers": [
                "Radiation resistance",
                "Turning tiny",
                "Radiation blast"
            ]
        },
        {
            "name": "Madame Uppercut",
            "age": 39,
            "secretIdentity": "Jane Wilson",
            "powers": [
                "Million tonne punch",
                "Damage resistance"
            ]
        }
    ]
}
```