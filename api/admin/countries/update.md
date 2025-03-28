# `PUT /api/v1/admin/countries/{country-id}`
You can update an existing country using this API.


## Permissions
- `countries.update`: to update a country

## Params

- `name`: Name of the country (required|maxlength:255)

## Response

### 200 OK

```json
{
    "country": {<country resource>},
}
```

[Country Resource](../../resources/country.md)

### 422 Unprocessable Entity
 [Validation error](../../validation-errors.md)

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)
