# Rating Resource

Represents a rating entity, including the user, ratable association, and score.


---

## Schema
| Field         | Type    | Description                                 |
|-------------- |---------|---------------------------------------------|
| id            | int     | Unique identifier for the rating            |
| user_id       | int     | ID of the user who created the rating       |
| ratable_type  | string  | Type of the ratable (e.g., `App\\Models\\Gym`) |
| ratable_id    | int     | ID of the ratable item                      |
| score         | int     | Score given (1-5)                           |

---

## Example
```json
{
  "id": 123,
  "user_id": 42,
  "ratable_type": "App\\Models\\Gym",
  "ratable_id": 10,
  "score": 5
}
```
