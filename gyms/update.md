# PUT /api/v1/gyms/{gym-id}

Updates the information of a specific gym by its ID. All parameters are optional; only provided fields will be updated. You can set fields to null to clear them.


---

## Permissions
| Permission              | Description                                         |
|-------------------------|-----------------------------------------------------|
| `gyms.update`           | Update your own gym                                 |
| `gyms.update_any`       | Update any gym as an admin                          |
| `gyms.transfer_ownership`| Transfer gym ownership (for `user_id` field)        |
| `gyms.approve_license`  | Approve or reject the gym license (for `gym_license_approved` / `gym_license_rejection_reason`) |

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym to update| 123     |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                                                 | Example           |
|--------------|---------|----------|-----------------------------------------------------------------------------|-------------------|
| name         | string  | No       | Name of the gym (max 255 characters)                                        | "Iron Paradise"  |
| address      | string  | No       | Address of the gym (max 255 characters)                                     | "123 Main St"    |
| location_lat | float   | No       | Latitude coordinate of the gym                                              | 35.6892           |
| location_lng | float   | No       | Longitude coordinate of the gym                                             | 51.3890           |
| is_active    | bool    | No       | Whether the gym is active                                                   | true              |
| show_crowd   | bool    | No       | Whether to display crowd information                                        | false             |
| description  | string  | No       | Description of the gym (max 2000 characters)                                | "Best gym..."    |
| user_id      | int     | No       | User ID to assign the gym to (requires `gyms.transfer_ownership` permission)| 42                |
| city_id      | int     | No       | ID of the city where the gym is located                                     | 5                 |
| major_ids    | string  | No       | Comma-separated list of major IDs. Use `0` to detach all majors.            | "1,2,3"          |
| gym_license_image | null | No | Only `null` is accepted, which clears the license document and resets its approval to pending. To **upload** a license, use [POST /api/v1/media](../media/create.md) with `purpose=gym_license`. Any non-null value is a validation error. | null |
| gym_license_approved | bool | No | Review outcome: `true` approved, `false` rejected, `null` pending. Requires `gyms.approve_license`. | true |
| gym_license_rejection_reason | string | No | Why the license was rejected (max 2000 characters). Requires `gyms.approve_license`. | "Document expired." |

> **License review.** `gym_license_approved` and `gym_license_rejection_reason` may only be sent by a user with `gyms.approve_license`; anyone else gets `403`. Setting `gym_license_approved` to `true` or `false` (a change from its previous value) notifies the gym owner. Clearing `gym_license_image` deletes the stored document and resets both review fields to `null`.

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

### 200 OK
Returns the updated gym resource.

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
    "updated_at": "2023-01-01 10:10:00",
    "show_crowd": false,
    "crowd": null,
    "city": {
      "id": 5,
      "name": "Tehran",
      "state": { "id": 1, "name": "Tehran Province" }
    },
    "majors": [
      { "id": 1, "title": "Bodybuilding" },
      { "id": 2, "title": "Crossfit" }
    ],
    "working_periods": [],
    "working_status": null,
    "boost": null,
    "media": [],
    "rating_count": 0,
    "rating_average": 0
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
| 403    | Forbidden (no permission, including reviewing a license without `gyms.approve_license`) | [Permission error](../_globals/permission-errors.md) |
