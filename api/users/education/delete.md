# `DELETE /api/v1/users/{user-id}/education/{education-id}`
You can delete an education from a user using this API.


## Permissions

- `education.delete`: deleting your own education
- `education.delete_any`: deleting education from any user

## Params

No parameter.

## Response

### 204 No Content
 No content when education gets deleted

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
