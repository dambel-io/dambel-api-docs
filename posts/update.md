# PUT /api/v1/posts/{post-id}

Updates a post by its ID. All parameters are optional; only provided fields will be updated.


---

## Permissions
| Permission         | Description                  |
|--------------------|------------------------------|
| `posts.update`     | Update your own post         |
| `posts.update_any` | Update any post (admin only) |

---

## Path Parameters
| Name    | Type | Required | Description             | Example |
|---------|------|----------|-------------------------|---------|
| post-id | int  | Yes      | ID of the post to update| 123     |

---

## Request Body Parameters
| Name     | Type   | Required | Description                                                                    | Example         |
|----------|--------|----------|--------------------------------------------------------------------------------|-----------------|
| title    | string | No       | Title of the post (max 255 characters)                                         | "My Workout"   |
| content  | string | No       | Content of the post (max 2000 characters)                                      | "Did squats..."|
| is_draft | bool   | No       | Whether the post is a draft                                                    | false           |
| in_blog  | bool   | No       | Publish the post on the website blog (requires `posts.update_any` permission)  | false           |

---

## Request Example
```json
{
  "title": "My Workout",
  "content": "Did squats and deadlifts.",
  "is_draft": false
}
```

---

## Response

### 200 OK
Returns the updated post resource.

```json
{
  "data": {
    "id": 123,
    "profile_type": "App\\Models\\User",
    "profile_id": 42,
    "title": "My Workout",
    "content": "Did squats and deadlifts.",
    "is_draft": false,
    "media": []
  }
}
```

See [Post Resource](post_resource.md).

---

### Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../_globals/not-found-errors.md)           |
