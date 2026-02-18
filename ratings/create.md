# POST /api/v1/ratings

Sets the authenticated user's rating for a specified element (gym or training service). If the user has not rated the element yet, a new rating is created. If they have already rated it, the existing rating is updated with the new score.


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
Returned when a new rating was created. Returns the created rating resource.

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

### 200 OK
Returned when the user already had a rating for this element and it was updated. Returns the updated rating resource.

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
