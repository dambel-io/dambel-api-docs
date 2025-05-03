# `PUT /api/v1/admin/countries/{country-id}`
You can update an existing country using this API.


## Permissions

- `countries.view_all`: to access countries
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

[Country Resource](country_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
