# `GET /api/v1/gyms/{gym-id}/peak-houes`
You can get peak hours graph data for a gym in a specific weekday in a specific date range using this API.


## Permissions

- `gyms.view_any`: to view data reports for all of the gyms if you are not the owner of the gym

## Params

- `weekday`: Name of the weekday that you want to get the data for
- `start_date`: Required start date for date range
- `end_date`: Required end date for date range

## Response

### 200 OK

```json
{
    "monday":    {"00": 15, "01": 15, "02": 15, "...": 15, "22": 15, "23": 15},
}
```

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
