# Tracker Progress Photo Resource

Represents one progress-photo entry in the tracker system.


---

## Schema
| Field        | Type           | Description                                                  |
|--------------|----------------|--------------------------------------------------------------|
| `id`         | integer        | Progress-photo record ID                                     |
| `user_id`    | integer        | User ID                                                      |
| `tracked_at` | string         | Datetime of the record (YYYY-MM-DD HH:MM:SS)                 |
| `pose`       | string \| null | `front`, `side`, `back` or `other`                           |
| `notes`      | string \| null | Notes                                                        |
| `media`      | array          | Attached images. See [Media Resource](../../media/create.md) |

## Access

The image is gated by exactly the rule that gates the entry. A viewer reading through a tracker
share can fetch the `media` link only while that share has `include_progress_photo = true` **and**
the entry's `tracked_at` falls inside the share's window; revoking the flag closes an already-known
URL on the next request. Anyone else — including an authenticated user with no share — gets 403 on
the media URL, not just on this resource.

---

## Example
```json
{
  "id": 123,
  "user_id": 7,
  "tracked_at": "2026-09-04 08:00:00",
  "pose": "front",
  "notes": "week 4",
  "media": [
    { "id": 91, "attachable_type": "App\\Models\\Tracker\\ProgressPhotos\\TrackerProgressPhoto", "attachable_id": 123, "link": "/api/v1/media/91/abc.jpg" }
  ]
}
```

---
