# POST /api/v1/ratings

Creates a new rating for a specified element (gym or training service).


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| view (ratable)     | Must have view permission on the ratable     |
| `ratings.create`   | Rate an element                             |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                                                 | Example         |
|--------------|---------|----------|-----------------------------------------------------------------------------|-----------------|
| ratable_type | string  | Yes      | Type of the element (`gym` or `training_service`)                            | "gym"          |
| ratable_id   | int     | Yes      | ID of the element to rate                                                    | 10              |
| score        | int     | Yes      | Score between 1 and 5                                                        | 5               |

---

## Request Example
```json
{
  "ratable_type": "gym",
  "ratable_id": 10,
  "score": 5
}
```

---

## Response

### 201 Created
Returns the created rating resource.

#### Example
```json
{
  "rating": {
    "id": 123,
    "user_id": 42,
    "ratable_type": "App\\Models\\Gym",
    "ratable_id": 10,
    "score": 5
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
