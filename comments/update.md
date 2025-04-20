# `PUT /api/v1/comments/{comment-id}`
You can update comments using this API.


## Permissions

- `comments.update`: To update your own comment

## Params

- `content`: Required content of the comment (max length 255)

## Response

### 200 OK
:
```json
{
    "comment": {<comment resource>},
}
```

[Comment Resource](../resources/comment.md)

### 422 Unprocessable Entity
[Validation error](../validation-errors.md)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)
