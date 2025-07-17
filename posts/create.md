# POST /api/v1/posts

Creates a new post for a specified profile (gym or user).


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `posts.create`     | Create posts for your own profiles  |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                                                 | Example         |
|--------------|---------|----------|-----------------------------------------------------------------------------|-----------------|
| profile_type | string  | Yes      | Type of the profile (`gym` or `user`)                                       | "user"         |
| profile_id   | int     | Yes      | ID of the profile to post to                                                | 42              |
| title        | string  | Yes      | Title of the post (max 255 characters)                                      | "My Workout"   |
| content      | string  | Yes      | Content of the post (max 255 characters)                                    | "Did squats..."|
| is_draft     | bool    | No       | Whether the post is a draft                                                 | false           |

---

## Request Example
```json
{
  "profile_type": "user",
  "profile_id": 42,
  "title": "My Workout",
  "content": "Did squats and deadlifts.",
  "is_draft": false
}
```

---

## Response

### 201 Created
Returns the created post resource.

#### Example
```json
{
  "post": {
    "id": 123,
    "profile_type": "App\\Models\\User",
    "profile_id": 42,
    "title": "My Workout",
    "content": "Did squats and deadlifts.",
    "is_draft": false
  }
}
```

For a full schema, see [Post Resource](post_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
