# POST /api/v1/gyms/{gym-id}/buffet-items

Creates a new buffet item for a gym.


---

## Permissions
| Permission                | Description                                         |
|---------------------------|-----------------------------------------------------|
| `buffet_items.create`     | Create buffet items for your own gym                |
| `buffet_items.create_any` | Create buffet items for any gym (admin only)        |

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym         | 123     |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                 | Example         |
|-------------|---------|----------|---------------------------------------------|-----------------|
| title       | string  | Yes      | Title of the item (max 255 characters)      | "Protein Bar"  |
| description | string  | No       | Description for the item (max 2000 chars)   | "Tasty bar"    |
| price       | int     | Yes      | Price of the item                           | 100             |
| discount    | float   | No       | Discount percentage (default 0)             | 10.5            |

---

## Request Example
```json
{
  "title": "Protein Bar",
  "description": "Tasty bar",
  "price": 100,
  "discount": 10.5
}
```

---

## Response

### 201 Created
Returns the created gym buffet item resource.

#### Example
```json
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
```

For a full schema, see [Gym Buffet Item Resource](gym_buffet_item_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
