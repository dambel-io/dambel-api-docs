# POST /api/v1/media

Attach a media file to a specified element (e.g., gym, post, user).


---

## Permissions
You must have **update** permission for the target attachable resource.

---

## Request Body Parameters
| Name            | Type    | Required | Description                                                      | Example         |
|-----------------|---------|----------|------------------------------------------------------------------|-----------------|
| attachable_type | string  | Yes      | Type of the element to attach media to (see below)               | "gym"          |
| attachable_id   | int     | Yes      | ID of the element                                                | 42              |
| file            | file    | Yes      | The media file to upload                                         | (binary file)   |

**Available `attachable_type` values:**
- `championship`
- `gym`
- `gym_equipment`
- `post`
- `user`
- `education`
- `gym_buffet_item`
- `training_service`

---

## Request Example (multipart/form-data)
```
POST /api/v1/media
Authorization: Bearer {token}
Content-Type: multipart/form-data

attachable_type=gym
attachable_id=42
file=@photo.jpg
```

---

## Response

### 201 Created
Returns the created media resource.

#### Example
```json
{
  "media": { /* media resource */ }
}
```

For a full schema, see [Media Resource](media_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
