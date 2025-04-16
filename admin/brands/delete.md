# `DELETE /api/v1/admin/brands/{brand-id}`
You can delete a brand using this endpoint.


## Permissions
- `brands.delete`: to delete any brand

## Params

- `replacement_id`: In case the brand you are deleting has some data attached to it, you transfer the data to another brand by providing it's ID in this optional parameter

## Response

### 204 No Content
 No content when brand gets deleted

### 400 Bad Request
 When brand has data and `replacement_id` is not provided or is not valid. Number of the attached items is returned in `attached_data`.

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
