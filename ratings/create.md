# `POST /api/v1/ratings`
You can rate an element using this API.


## Permissions

- You need to have **view** permission of the **ratable**
- `ratings.create`: To rate something

## Params

- `ratable_type`: Type of the element that you are rating. These are available items:
  - `gym`
  - `training_service`
- `ratable_id`: Id of the element
- `score`: The score between 1 and 5

## Response

### 201 Created
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
