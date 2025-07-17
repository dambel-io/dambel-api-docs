# GET /api/v1/gyms

Retrieves a list of gyms, with support for filtering by location, owner, major, and more. Results can be sorted by proximity, marketing boosts, or recency.


---

## Permissions
| Permission      | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `gyms.view_all` | View all gyms, including inactive ones (admin only). Without this, only active gyms are returned. |

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example         |
|-----------|--------|----------|-----------------------------------------------------------------------------|-----------------|
| city_id   | int    | No       | City ID(s) to filter by (comma-separated for multiple)                      | "1,2,3"        |
| state_id  | int    | No       | State ID(s) to filter by (comma-separated for multiple)                     | "4,5"          |
| country_id| int    | No       | Country ID(s) to filter by (comma-separated for multiple)                    | "6"            |
| gym_id    | int    | No       | Specific gym ID(s) to fetch (comma-separated for multiple)                   | "10,11"        |
| user_id   | int    | No       | Owner user ID(s) to filter by (comma-separated for multiple)                 | "42"           |
| major_id  | int    | No       | Major ID(s) to filter by (comma-separated for multiple)                      | "1,2"          |
| word      | string | No       | Search gyms by text                                                          | "fitness"      |
| page      | int    | No       | Page number for pagination                                                   | 1               |
| lat       | float  | No       | Latitude for proximity search                                                | 35.6892         |
| lng       | float  | No       | Longitude for proximity search                                               | 51.3890         |
| radius    | float  | No       | Radius in kilometers for proximity search (default: 50, min: 10, max: 900000)| 50              |

Results are sorted by marketing boosts first, then by proximity (if `lat`/`lng` provided), otherwise by newest.

> If you specify location parameters, pagination is removed and all results within the radius are returned in one page.

---

## Response

### 200 OK
Returns a paginated list of gym resources.

#### Schema
```json
{
  "data": [
    { /* Gym Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

#### Example
```json
{
  "data": [
    {
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
        "state": {
          "id": 1,
          "name": "Tehran Province"
        }
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
  ],
  "links": {
    "first": "https://api.example.com/api/v1/gyms?page=1",
    "last": "https://api.example.com/api/v1/gyms?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/gyms?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/gyms",
    "per_page": 30,
    "to": 30,
    "total": 300
  }
}
```

For a full schema, see [Gym Resource](gym_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
