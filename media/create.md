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
| purpose         | string  | No       | Marks the upload as a sensitive document instead of ordinary gallery media (see below) | "gym_license"   |

**Available `purpose` values:**

| Value             | Attachable       | Meaning                                                                 |
|-------------------|------------------|-------------------------------------------------------------------------|
| `trainer_license` | `user`           | The uploader's own trainer license. May only be attached to your own user record. |
| `gym_license`     | `gym`            | The gym's business license. May only be attached to a gym you are allowed to update. |

> **Sensitive media.** A media row with a `purpose` is never publicly downloadable — [GET /api/v1/media/{media}/{filename}](download.md) applies per-purpose access control to it, and it is excluded from the owning record's public `media` array. Uploading a license also points the owning record's `*_license_image` at the new file, deletes the superseded document, and resets `*_license_approved` to `null` (pending), because a new document has to be reviewed again — this applies to both `trainer_license` (on the user) and `gym_license` (on the gym). Omitting `purpose` (or sending `null`) uploads ordinary, publicly readable gallery media.

**Available `attachable_type` values:**
- `championship`
- `gym`
- `gym_equipment`
- `post`
- `user`
- `education`
- `gym_buffet_item`
- `training_service`
- `tracker_meal`

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

### 200 OK
Returns the created media resource.

#### Example
```json
{
  "data": { /* media resource */ }
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
