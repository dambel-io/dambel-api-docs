# PUT /api/v1/admin/cities/{city-id}

Update an existing city.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |
| `cities.update`    | Update a city       |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the city (max 255)         |
| `location_lat` | number\|null | With `location_lng` | Latitude of the city centre, between `-90` and `90`. `null` clears it. |
| `location_lng` | number\|null | With `location_lat` | Longitude of the city centre, between `-180` and `180`. `null` clears it. |

The coordinates are set or cleared together. Omit both to keep the stored centre. Sending only one of them, or one
value and one `null`, is a 422 naming the other field, so a city can never be left with half a coordinate. A city
without coordinates is not a target for [`GET /admin/cities/resolve`](resolve.md) or for deriving a gym's city.

---

## Response

### 200 OK
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
