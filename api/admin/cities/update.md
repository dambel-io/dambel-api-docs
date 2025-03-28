# `PUT /api/v1/admin/cities/{city-id}`
You can update an existing city using this API.


### Permissions
- `cities.update`: to update a city

### Params

- `name`: Name of the city (required|maxlength:255)

### Response

200:
```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
