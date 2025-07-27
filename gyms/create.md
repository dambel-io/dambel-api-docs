# POST /api/v1/gyms

Creates a new gym. This endpoint can be used by regular users to create their own gym, or by admins to create gyms for other users.


---

## Permissions
| Permission      | Description                                      |
|---------------------|--------------------------------------------------|
| `gyms.create`       | Create your own gym                              |
| `gyms.create_any`   | Create a gym for another user (admin only)       |

---

## Request Parameters

| Name         | Type    | Required | Description                                                                 | Example           |
|--------------|---------|----------|-----------------------------------------------------------------------------|-------------------|
| name         | string  | Yes      | Name of the gym (max 255 characters)                                        | "Iron Paradise"  |
| address      | string  | Yes      | Address of the gym (max 255 characters)                                     | "123 Main St"    |
| location_lat | float   | Yes      | Latitude coordinate of the gym                                              | 35.6892           |
| location_lng | float   | Yes      | Longitude coordinate of the gym                                             | 51.3890           |
| is_active    | bool    | No       | Whether the gym is active                                                   | true              |
| show_crowd   | bool    | No       | Whether to display crowd information                                        | false             |
| description  | string  | No       | Description of the gym (max 2000 characters)                                | "Best gym..."    |
| user_id      | int     | No       | User ID to assign the gym to (requires `gyms.create_any` permission)        | 42                |
| city_id      | int     | Yes      | ID of the city where the gym is located                                     | 5                 |
| major_ids    | string  | No       | Comma-separated list of major IDs. Use `0` to detach all majors.            | "1,2,3"          |

---

## Request Example

```json
{
  "name": "Iron Paradise",
  "address": "123 Main St",
  "location_lat": 35.6892,
  "location_lng": 51.3890,
  "is_active": true,
  "show_crowd": false,
  "description": "A premium gym with modern equipment.",
  "user_id": 42,
  "city_id": 5,
  "major_ids": "1,2,3"
}
```

---

## Response

### 201 Created
Returns the created gym resource.

#### Schema
```json
{
  "gym": { /* Gym Resource */ }
}
```

#### Example
```json
{
  "gym": {
    "id": 123,
    "name": "Iron Paradise",
    "address": "123 Main St",
    "location_lat": 35.6892,
    "location_lng": 51.3890,
    "is_active": true,
    "description": "A premium gym with modern equipment.",
    "created_at": "2023-01-01 10:00:00",
    "updated_at": "2023-01-01 10:00:00",
    "show_crowd": false,
    "crowd": null,
    "city": {
      "id": 5,
      "name": "Tehran",
      "state": { /* State Resource */ }
    },
    "majors": [
      { "id": 1, "title": "Bodybuilding" },
      { "id": 2, "title": "Crossfit" }
    ],
    "working_periods": [
      {
        "id": 1,
        "gym_id": 123,
        "day": "monday",
        "gender": "women",
        "opens_at": "07:00",
        "closes_at": "23:30",
        "description": "Morning shift",
        "is_exception": false,
        "exception_start_date": null,
        "exception_end_date": null
      }
    ],
    "working_status": {
      "current": {
        "gender": "genderless",
        "opens_at": "08:30",
        "closes_at": "23:00"
      }
    },
    "boost": null,
    "media": [
      {
        "id": 10,
        "attachable_type": "App\\Models\\Gyms\\Gym",
        "attachable_id": 123,
        "link": "https://example.com/media/10.jpg"
      }
    ],
    "rating_count": 12,
    "rating_average": 4.5
  }
}
```

For a full schema, see [Gym Resource](gym_resource.md).

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
