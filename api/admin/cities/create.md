# `POST /api/v1/admin/cities/{state}`
This API creates a new city.


### Permissions

- `cities.create`: to create a city

### Params

- `name`: Name of the city (required|maxlength:255)
- ID of the state in the route

### Response

201:
```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
