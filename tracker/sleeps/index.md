# `GET /api/v1/tracker/sleeps`
You can get a list of sleep records in the tracker system.


## Permissions

- `tracker_sleeps.view`: viewing tracker sleep

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
        {<tracker sleep resource>},
        {<tracker sleep resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Tracker Sleep Resource](tracker_sleep_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
