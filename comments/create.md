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
- `parent_comment_id`: If the comment is in reply to another comment, its id can be sent here

## Response

### 201 Created
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
