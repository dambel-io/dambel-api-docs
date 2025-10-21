# `GET /api/v1/admin/stats`

Retrieve admin statistics including counts of users, gyms, and trainers.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `users.view_all`      | Access admin stats  |

---

## Response

### 200 OK
```json
{
  "users_count": 123,
  "gyms_count": 45,
  "trainers_count": 67
}
```

---

## Schema
| Field          | Type    | Description                                 |
|----------------|---------|---------------------------------------------|
| `users_count`  | integer | Total number of registered users            |
| `gyms_count`   | integer | Total number of gyms                        |
| `trainers_count`| integer | Total number of training services          |

---
