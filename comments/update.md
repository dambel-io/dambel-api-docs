# `PUT /api/v1/comments/{comment-id}`
You can update comments using this API.


## Permissions

- `comments.update`: To update your own comment

## Params

- `content`: Required content of the comment (max length 255)

## Response

### 200 OK
```json
{
    "comment": {<comment resource>},
}
```

[Comment Resource](comment_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
