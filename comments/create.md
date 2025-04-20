# `POST /api/v1/comments`
You can create comment using this API.


## Permissions

- `comments.create`: To create comments from yourself
- view permission of **commentable**

## Params

- `commentable_type`: Type of the element that you are adding comment to. These are available items:
  - `gym`
  - `post`
  - `trainingService`
- `commentable_id`: Id of the element
- `content`: Required content of the comment (max length 255)

## Response

### 201 Created
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
