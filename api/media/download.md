# `GET /api/v1/media/{media-id}`
You can download a media using this API.


## Permissions
You need to have **view** permission of the **imagable**.

## Response

### 200 OK
The media file will be returned.

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
