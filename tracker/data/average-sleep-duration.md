# `GET /api/v1/tracker/data/average-sleep-duration`
You can get your average sleep duration using this API.


## Params

- `start_date`: Start of the date range (optional)
- `end_date`: End of the date range (optional)
- `shared_tracker_slug`: Optional slug of a shared tracker record. If not set, your own tracker data will be used
- `search`: Search based on notes

## Response

### 200 OK

```json
{
    "average_sleep_duration": "07:34"
}
```

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
