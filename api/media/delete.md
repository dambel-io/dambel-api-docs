# `DELETE /api/v1/media/{media-id}`
You can delete an attached media of any element using this API.


## Permissions
You need to have **update** permission of the **imagable**.

## Params

- `id`: ID of the gym in the route

## Response

### 204 No Content
No content when media gets deleted

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
