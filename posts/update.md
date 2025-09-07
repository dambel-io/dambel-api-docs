# PUT /api/v1/posts/{post-id}

Updates a post by its ID. All parameters are optional; only provided fields will be updated. You can set fields to null to clear them.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| `posts.update`     | Update your own post                        |
| `posts.update_any` | Update any post (admin only)                |

---

## Path Parameters
| Name     | Type | Required | Description           | Example |
|----------|------|----------|-----------------------|---------|
| post-id  | int  | Yes      | ID of the post to update| 123     |

---

## Request Body Parameters
| Name    | Type   | Required | Description                                 | Example         |
|---------|--------|----------|---------------------------------------------|-----------------|
| title   | string | No       | Title of the post (max 255 characters)      | "My Workout"   |
| content | string | No       | Content of the post (max 255 characters)    | "Did squats..."|
| is_draft| bool   | No       | Whether the post is a draft                 | false           |
| in_blog | bool   | No       | Publish the post on the website blog. Only users with `posts.update_any` permission can do it                 | false           |

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
