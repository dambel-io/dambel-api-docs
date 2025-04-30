# `DELETE /api/v1/posts/{post-id}`
You can delete a post using this API.


## Permissions

- You need to have **view** permission of the **profile**
- `posts.delete`: To delete your own posts
- `posts.delete_any`: To delete any post

## Response

### 204 No Content
No content when post gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
