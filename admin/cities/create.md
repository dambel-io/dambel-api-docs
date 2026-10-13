# POST /api/v1/admin/cities/{state}

Create a new city in a given state.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |
| `cities.create`    | Create a city       |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the city (max 255)         |
| `location_lat` | number\|null | With `location_lng` | Latitude of the city centre, between `-90` and `90` |
| `location_lng` | number\|null | With `location_lat` | Longitude of the city centre, between `-180` and `180` |

The coordinates are optional, but send both or neither: sending one without the other is a 422 naming the missing
field. A city with coordinates becomes a target for [`GET /admin/cities/resolve`](resolve.md) and for deriving a
gym's city from its map pin; a city without them is never resolved to.

*The state ID is provided in the route.*

---

## Response

### 201 Created
```json
{
  "data": { /* city resource */ }
}
```
- [City Resource](city_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
