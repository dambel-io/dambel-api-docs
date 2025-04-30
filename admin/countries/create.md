# `POST /api/v1/admin/countries`
This API creates a new country.


## Permissions
- `countries.create`: to create a country

## Params

- `name`: Name of the country (required|maxlength:255)

## Response

### 201 Created
```json
{
    "country": {<country resource>},
}
```

[Country Resource](country_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
