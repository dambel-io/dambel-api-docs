# POST /api/v1/tracker/shares

Create a new shared tracker configuration to share tracker data with another user.


---

## Permissions
| Permission               | Description             |
|--------------------------|-------------------------|
| `shared_trackers.create` | Create shared tracker   |

---

## Request Body Parameters
| Name                 | Type    | Required | Description                                                         |
|----------------------|---------|----------|---------------------------------------------------------------------|
| `viewer_user_id`     | integer | Yes      | ID of the user to share tracker data with                           |
| `start_date`         | string  | No       | Start date for the sharing period (YYYY-MM-DD) or null              |
| `end_date`           | string  | No       | End date for the sharing period (YYYY-MM-DD) or null                |
| `include_wakeup`     | boolean | No       | Whether to include wakeup data (default: true)                      |
| `include_weight`     | boolean | No       | Whether to include weight data (default: true)                      |
| `include_water`      | boolean | No       | Whether to include water intake data (default: true)                |
| `include_sleep`      | boolean | No       | Whether to include sleep data (default: true)                       |
| `include_supplement` | boolean | No       | Whether to include supplement data (default: true)                  |
| `include_meal`       | boolean | No       | Whether to include meal data (default: true)                        |
| `include_workout`    | boolean | No       | Whether to include workout data (default: true)                     |
| `include_measurement` | boolean | No      | Whether to include body-measurement data (default: true)            |
| `include_progress_photo` | boolean | No   | Whether to include progress photos (**default: false** — see below) |
| `notify_wakeup`      | boolean | No       | Whether to notify when the owner logs a wakeup (default: false)     |
| `notify_weight`      | boolean | No       | Whether to notify when the owner logs their weight (default: false)  |
| `notify_water`       | boolean | No       | Whether to notify when the owner logs water intake (default: false) |
| `notify_sleep`       | boolean | No       | Whether to notify when the owner logs sleep (default: false)        |
| `notify_supplement`  | boolean | No       | Whether to notify when the owner logs a supplement (default: false) |
| `notify_meal`        | boolean | No       | Whether to notify when the owner logs a meal (default: false)       |
| `notify_workout`     | boolean | No       | Whether to notify when the owner logs a workout (default: false)    |
| `description`        | string  | No       | Optional description for the shared tracker (max 2000 characters)   |

> **Note:** If both `start_date` and `end_date` are provided, `end_date` must be after `start_date`. When both are `null`, all tracker data is shared without date restrictions.

> **`include_progress_photo` is the one flag that defaults to `false`.** Every other type follows
> "a share covers everything unless the athlete unchecks it". A body photo of an identifiable
> person is opted into, never opted out of, so a share grants access to progress photos only when
> this flag is sent as `true`. A share-editing UI that assumes a uniform default will mis-render
> it. The flag governs the **image** as well as the entry: with it off, the media URL of a
> progress photo returns 403 to that viewer.

> **`include_measurement` defaults to `true` for shares that already existed.** The column was
> added with a `true` default, so every share created before this feature shipped covers body
> measurements without its sharer doing anything. Nothing was retroactively disclosed — body
> measurements are a new record type, so none existed when the column landed — but a sharer who
> does not want the new type shared turns the flag off with
> `PUT /api/v1/tracker/shares/{id}`. A client that lists shares should not assume an existing
> share's flags are unchanged from when it was made.

> **`notify_*` flags are not accepted here.** They belong to the viewer, who sets them with
> `PUT /api/v1/tracker/shares/{id}`. They are stored as `false` and this response returns them as
> `null` — the freshly-inserted row has not read its column defaults back. Read the share back
> through `GET /api/v1/tracker/shares` for their real values.

> **One share per pair of people.** Posting again for a `viewer_user_id` you already share with
> **updates that share** and returns it, rather than creating a second one — so the endpoint is
> safe to re-submit, and "the share with this person" always names exactly one row. The status is
> `201` either way, and the viewer is notified only when a share is actually created, not on a
> re-submit. An omitted `include_*` flag defaults to `true` on every call, so a repeat post
> rewrites the whole grant rather than patching it; the `notify_*` flags and the dates are left as
> they were unless you send them. To change one field, use `PUT /api/v1/tracker/shares/{id}`.

---

## Request Example
```json
{
  "viewer_user_id": 456,
  "start_date": "2024-01-01",
  "end_date": "2024-01-31",
  "description": "January fitness tracking data",
  "include_wakeup": true,
  "include_weight": false,
  "include_water": true,
  "include_sleep": true,
  "include_supplement": false,
  "include_meal": true,
  "include_workout": true,
  "include_measurement": true,
  "include_progress_photo": true
}
```

---

## Response

### 201 Created
Returns the created shared tracker resource.

```json
{ /* shared tracker resource */ }
```

See [Shared Tracker Resource](shared_tracker_resource.md).

---

## Error Responses
| Status | Description       | Reference                                                       |
|--------|-------------------|-----------------------------------------------------------------|
| 422    | Validation error  | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized      | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden         | [Permission error](../../_globals/permission-errors.md)         |
