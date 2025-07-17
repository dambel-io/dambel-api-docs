# PUT /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}

Updates a buffet item for a gym. All parameters are optional; only provided fields will be updated. You can set fields to null to clear them.


---

## Permissions
| Permission                    | Description                                         |
|-------------------------------|-----------------------------------------------------|
| `gym_buffet_items.update`     | Update buffet items for your own gym                |
| `gym_buffet_items.update_any` | Update buffet items for any gym (admin only)        |

---

## Path Parameters
| Name           | Type | Required | Description                | Example |
|----------------|------|----------|----------------------------|---------|
| gym-id         | int  | Yes      | ID of the gym              | 123     |
| buffet-item-id | int  | Yes      | ID of the buffet item      | 5       |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                 | Example         |
|-------------|---------|----------|---------------------------------------------|-----------------|
| title       | string  | No       | Title of the item (max 255 characters)      | "Protein Bar"  |
| description | string  | No       | Description for the item (max 2000 chars)   | "Tasty bar"    |
| price       | int     | No       | Price of the item                           | 100             |
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

### 200 OK
Returns the updated gym buffet item resource.

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
