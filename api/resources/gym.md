# Gym Resource

- [`App\Http\Resources\V1\GymResource`](../../../src/app/Http/Resources/V1/GymResource.php)

```json
{
    "id": 123,
    "name": "...",
    "address": "...",
    "location_lat": 123.456,
    "location_lng": 123.456,
    "is_active": true,
    "description": "...",
    "created_at": "1970-01-01 00:00:00",
    "updated_at": "1970-01-01 00:00:00",
    "show_crowd": true,
    "crowd": 123,
    "city": <city resource>,
    "majors": [<major resource>, <major resource>, ...],
    "working_periods": [<working period resource>, ...],
    "working_status": <explained below>
}
```

[City Resource](city.md)

[Major Resource](major.md)

[Working Period Resource](gym_working_period.md)

### Working status
The `working_status` field can give you some information about the current working status of the gym at that day and time.

There are 4 scenarios for that:

1. The value is `null` which means the gym does not work on that day

2. The value will be an object with key `current` which means the gym is currently working. The content includes gender, opens at, and closes at values (from the working period)

3. Same as above, but instead of current, it will have key `next` which means it's currently closed, but will open in future at that day

4. Similar as the other two, but key is `last`, which means the gym was open a few hours ago but is closed and finished it's working period for today

The value of all of `current`, `next`, and `last` keys would be something like this:

```json
{
    "working_status": {
        "current": {
            "gender": "genderless",
            "opens_at": "08:30",
            "closes_at": "23:00"
        },
        "next": {
            "gender": "genderless",
            "opens_at": "08:30",
            "closes_at": "23:00"
        },
        "last": {
            "gender": "genderless",
            "opens_at": "08:30",
            "closes_at": "23:00"
        }
    }
}
```

Only one of these three keys will be there. The json shown above includes all of them just as an example.
