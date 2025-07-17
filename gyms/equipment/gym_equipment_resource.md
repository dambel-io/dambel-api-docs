# Gym Equipment Resource

Represents a piece of equipment assigned to a gym, including its type, brand, count, description, and associated media.


---

## Schema
| Field       | Type    | Description                                 | Example                |
|-------------|---------|---------------------------------------------|------------------------|
| id          | int     | Unique identifier for the gym equipment      | 123                    |
| gym_id      | int     | ID of the gym                               | 123                    |
| equipment   | object  | Equipment resource object                    | { ... }                |
| brand       | object  | Brand resource object (nullable)             | { ... }                |
| count       | int     | Number of this equipment in the gym          | 5                      |
| description | string  | Description of the equipment (nullable)      | "some description"     |
| media       | array   | List of associated media resources           | [ { ... }, ... ]        |

---

## Example
```json
{
  "id": 123,
  "gym_id": 123,
  "equipment": { /* equipment resource */ },
  "brand": { /* brand resource */ },
  "count": 5,
  "description": "some description",
  "media": [ { /* media resource */ } ]
}
```

For media schema, see [Media Resource](../../media/media_resource.md).
