# Gym Resource

Represents a gym entity with all its attributes, relationships, and status information.


---

## Schema

| Field            | Type                | Description                                                                                 |
|------------------|---------------------|---------------------------------------------------------------------------------------------|
| id               | int                 | Unique identifier for the gym                                                               |
| name             | string              | Name of the gym                                                                            |
| address          | string              | Address of the gym                                                                         |
| location_lat     | float               | Latitude coordinate                                                                        |
| location_lng     | float               | Longitude coordinate                                                                       |
| is_active        | bool                | Whether the gym is active                                                                  |
| description      | string              | Description of the gym                                                                     |
| created_at       | string (datetime)   | Creation timestamp                                                                         |
| updated_at       | string (datetime)   | Last update timestamp                                                                      |
| show_crowd       | bool                | Whether crowd information is displayed                                                     |
| crowd            | int\|null           | Current crowd count (null if show_crowd is false)                                          |
| city             | City Resource       | City where the gym is located ([see here](../admin/cities/city_resource.md))               |
| majors           | Major Resource[]    | List of majors associated with the gym ([see here](../admin/majors/major_resource.md))     |
| working_periods  | Working Period[]    | List of working periods ([see here](working-periods/gym_working_period_resource.md))       |
| working_status   | object\|null        | Current working status (see below)                                                         |
| boost            | object\|null        | Marketing boost info ([see here](../payments/marketing_boost_resource.md))                 |
| media            | Media Resource[]    | List of media items ([see here](../media/media_resource.md))                               |
| rating_count     | int                 | Number of ratings                                                                          |
| rating_average   | float               | Average rating                                                                             |

---

## Example

```json
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
```

---

## Field Details

### working_status
The `working_status` field provides information about the gym's current operational status for the day. It can be:
- `null`: The gym is closed for the day.
- An object with one of the following keys:
  - `current`: The gym is currently open.
  - `next`: The gym is currently closed but will open later today.
  - `last`: The gym was open earlier but is now closed for the day.

Each status object contains:
```json
{
  "gender": "genderless",
  "opens_at": "08:30",
  "closes_at": "23:00"
}
```

### crowd
The `crowd` field shows the current number of people checked in at the gym, calculated from subscription check-ins/outs. If `show_crowd` is `false`, this value will be `null`.

---

## Related Resources
- [City Resource](../admin/cities/city_resource.md)
- [Major Resource](../admin/majors/major_resource.md)
- [Working Period Resource](working-periods/gym_working_period_resource.md)
- [Marketing Boost Resource](../payments/marketing_boost_resource.md)
- [Media Resource](../media/media_resource.md)
