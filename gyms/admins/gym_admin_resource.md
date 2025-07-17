# Gym Admin Resource

Represents a gym admin entity, including their title, user, permissions, and associated gym.


---

## Schema
| Field        | Type         | Description                                 |
|--------------|--------------|---------------------------------------------|
| id           | int          | Unique identifier for the gym admin          |
| gym_id       | int          | ID of the gym                               |
| title        | string       | Title of the admin                          |
| user_id      | int          | ID of the user who is the admin             |
| permissions  | string array | List of permission names for the admin      |

---

## Example
```json
{
  "id": 1,
  "gym_id": 123,
  "title": "Manager",
  "user_id": 42,
  "permissions": ["edit_gym", "view"]
}
```
