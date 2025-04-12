# `PUT /api/v1/ratings/{rating-id}`
You can update your previous rating using this API.


## Permissions

- `ratings.update`: To update your own rating

## Params

- `score`: The score between 1 and 5

## Response

### 200 OK
:
```json
{
    "rating": {<rating resource>},
}
```

[Rating Resource](../resources/rating.md)

### 422 Unprocessable Entity
[Validation error](../validation-errors.md)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)
