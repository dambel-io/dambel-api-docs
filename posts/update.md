# `PUT /api/v1/posts/{post-id}`
You can update posts using this API.


## Permissions

- `posts.update`: To update your own post
- `posts.update_any`: To update any post

## Params

- `title`: Required title of the post (max length 255)
- `content`: Required content of the post (max length 255)
- `is_draft`: A boolean to draft the post

## Response

### 200 OK
```json
{
    "post": {<post resource>},
}
```

[Post Resource](../resources/post.md)

### 422 Unprocessable Entity
[Validation error](../validation-errors.md)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)
