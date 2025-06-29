# `GET /api/v1/tracker/meals`
You can get a list of meal records in the tracker system.


## Permissions

- `tracker_meals.view`: viewing tracker meal

## Params

- `start_date`: Start of the date range (optional)
- `end_date`: End of the date range (optional)
- `shared_tracker_slug`: Optional slug of a shared tracker record. If not set, your own tracker data will be used
- `search`: Search based on notes
- `page`: Page number for pagination

## Response

### 200 OK

```json
{
    "data": [
        {<tracker meal resource>},
        {<tracker meal resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Tracker Meal Resource](tracker_meal_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
