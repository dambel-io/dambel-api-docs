# `PUT /api/v1/ratings/{rating-id}`
You can update your previous rating using this API.


## Permissions

- `ratings.update`: To update your own rating

## Params

- `score`: The score between 1 and 5

## Response

### 200 OK
```json
{
    "rating": {<rating resource>},
}
```

[Rating Resource](rating_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
