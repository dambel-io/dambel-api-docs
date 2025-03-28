# `POST /api/v1/admin/countries`
This API creates a new country.


### Permissions
- `countries.create`: to create a country

### Params

- `name`: Name of the country (required|maxlength:255)

### Response

201:
```json
{
    "country": {<country resource>},
}
```

[Country Resource](../../resources/country.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
