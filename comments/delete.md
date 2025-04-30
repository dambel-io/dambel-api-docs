# `DELETE /api/v1/comments/{comment-id}`
You can delete a comment using this API.


## Permissions

- You need to have **view** permission of the **commentable**
- `comments.delete`: To delete your own comments
- `comments.delete_any`: To delete any comment

## Response

### 204 No Content
No content when comment gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
