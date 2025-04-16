# `DELETE /api/v1/admin/majors/{major-id}`
You can delete a major using this endpoint.


## Permissions
- `majors.delete`: to delete any major

## Params

- `replacement_id`: In case the major you are deleting has some data attached to it, you transfer the data to another major by providing it's ID in this optional parameter

## Response

### 204 No Content
 No content when major gets deleted

### 400 Bad Request
 When major has data and `replacement_id` is not provided or is not valid. Number of the attached items is returned in `attached_data`.

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
