# GET /api/v1/tracker/wakeups
You can get a list of wakeup records in the tracker system.


## Permissions

- `tracker_wakeups.view`: viewing tracker wakeup

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
        {<tracker wakeup resource>},
        {<tracker wakeup resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Tracker Wakeup Resource](tracker_wakeup_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
