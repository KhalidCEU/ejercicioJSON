
## Ejercicio JSON Schema

[Enlace](https://jsonschema.dev/) al **validador** usado

**Solucion**

Fichero [json.json](/json.json)

### Enunciado

1. Crea un JSON que sea válido con el [siguiente JSON Schema](/schema.json):

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
