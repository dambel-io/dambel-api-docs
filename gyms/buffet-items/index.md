# GET /api/v1/gyms/{gym-id}/buffet-items

Retrieves a list of buffet items for a specific gym.


**No authentication required.**

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
