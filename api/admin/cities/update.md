# `PUT /api/v1/admin/cities/{city-id}`
You can update an existing city using this API.


## Permissions
- `cities.update`: to update a city

## Params

- `name`: Name of the city (required|maxlength:255)

## Response

### 200 OK

```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
