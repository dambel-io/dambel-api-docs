# State Resource

Represents a state in the system.


---

## Schema
| Field      | Type    | Description                                 |
|----------- |---------|---------------------------------------------|
| `id`       | integer | State ID                                    |
| `name`     | string  | State name                                  |
| `country`  | object  | [Country Resource](../countries/country_resource.md) |

---

## Example
```json
{
  "id": 123,
  "name": "...",
  "country": <country resource>
}
```

---
