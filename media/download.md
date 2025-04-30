# `GET /api/v1/media/{media-id}`
You can download a media using this API.


## Permissions
You need to have **view** permission of the **attachable**.

## Response

### 200 OK
The media file will be returned.

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
