# PUT /api/v1/ratings/{rating-id}

Updates a rating by its ID. Only the score can be updated.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| `ratings.update`   | Update your own rating                      |

---

## Path Parameters
| Name      | Type | Required | Description           | Example |
|-----------|------|----------|-----------------------|---------|
| rating-id | int  | Yes      | ID of the rating to update| 123     |

---

## Request Body Parameters
| Name  | Type | Required | Description                | Example |
|-------|------|----------|----------------------------|---------|
| score | int  | Yes      | Score between 1 and 5      | 4       |

---

## Request Example
```json
{
  "score": 4
}
```

---

## Response

### 200 OK
Returns the updated rating resource.

#### Example
```json
{
  "rating": {
    "id": 123,
    "user_id": 42,
    "ratable_type": "App\\Models\\Gym",
    "ratable_id": 10,
    "score": 4
  }
}
```

For a full schema, see [Rating Resource](rating_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
