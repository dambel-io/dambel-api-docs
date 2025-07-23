# City Resource

Represents a city in the system.


---

## Schema
| Field      | Type    | Description                                 |
|------------|---------|---------------------------------------------|
| `id`       | integer | City ID                                     |
| `name`     | string  | City name                                   |
| `state`    | object  | [State Resource](../states/state_resource.md)|

---

## Example
```json
{
  "id": 123,
  "name": "...",
  "state": <state resource>
}
```

---
