# `DELETE /api/v1/media/{media-id}`
You can delete an attached media of any element using this API.


## Permissions
You need to have **update** permission of the **attachable**.

## Response

### 204 No Content
No content when media gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
