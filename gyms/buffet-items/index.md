# GET /api/v1/gyms/{gym-id}/buffet-items

Retrieves a list of buffet items for a specific gym.


**No authentication required.**

---

## Permissions
| Permission      | Description                                             |
|-----------------|---------------------------------------------------------|
| `gyms.view_all` | Required to view buffet items for a gym that is inactive or whose license is not approved |

> A gym's public sub-resources are only served while the gym is active **and** its license is approved. The gym owner and holders of `gyms.view_all` are exempt; everyone else gets a 403. See [Gym List](../index.md).

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym         | 123     |

---

## Response

### 200 OK
Returns a list of gym buffet item resources.

#### Example
```json
{
  "data": [
    {
      "id": 1,
      "gym_id": 123,
      "title": "Protein Bar",
      "description": "Tasty bar",
      "price": 100,
      "discount": 10.5,
      "discounted_price": 89.5,
      "media": []
    }
  ]
}
```

For a full schema, see [Gym Buffet Item Resource](gym_buffet_item_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
