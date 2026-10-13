# City Resource

Represents a city in the system.


---

## Schema
| Field              | Type    | Description                                 |
|--------------------|---------|---------------------------------------------|
| `id`               | integer | City ID                                     |
| `name`             | string  | City name                                   |
| `translated_name`  | string  | Translated city name                        |
| `location_lat`     | number\|null | Latitude of the city centre; `null` when unknown  |
| `location_lng`     | number\|null | Longitude of the city centre; `null` when unknown |
| `state`            | object  | [State Resource](../states/state_resource.md)|

---

## Example
```json
{
  "id": 123,
  "name": "...",
  "translated_name": "...",
  "location_lat": 35.6944,
  "location_lng": 51.4215,
  "state": <state resource>
}
```

---
