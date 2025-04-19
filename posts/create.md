# `POST /api/v1/posts`
You can create post using this API.


## Permissions

- `posts.create`: To create post for your own profiles

## Params

- `profile_type`: Type of the element that you are adding post to. These are available items:
  - `gym`
  - `user`
- `profile_id`: Id of the element
- `title`: Required title of the post (max length 255)
- `content`: Required content of the post (max length 255)
- `is_draft`: A boolean to draft the post

## Response

### 201 Created
:
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
