# `GET /api/v1/users`

Retrieve a paginated list of users, with support for advanced filtering and sorting.


---

## Permissions
| Permission         | Description                |
|--------------------|----------------------------|
| `users.view_all`   | View all users             |

---

## Query Parameters
| Name           | Type     | Required | Description                                                                                 |
|----------------|----------|----------|---------------------------------------------------------------------------------------------|
| `page`         | integer  | No       | Page number for pagination                                                                  |
| `search`       | string   | No       | Search text in user's name, email, username, or phone                                                 |
| `email_status` | string   | No       | Filter by email verification status: `verified` or `not_verified`                           |
| `phone_status` | string   | No       | Filter by phone verification status: `verified` or `not_verified`                           |
| `user_id`      | array    | No       | Filter by one or more specific user IDs                                                     |
| `sort_by`      | string   | No       | Sort by: `name`, `email`, `phone`, `created_at`, `email_verified_at`, `phone_verified_at`   |
| `sort_order`   | string   | No       | Sort order: `desc` (default) or `asc`                                                       |

*Default sort is by `created_at` (newest first).*

---

## Response

### 200 OK
```json
{
  "data": [
    {<user resource>},
    ...
  ],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```

- [User Resource](user_resource.md)
- [Pagination Data](../_globals/pagination-data.md) (per page: 30)

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)

---
