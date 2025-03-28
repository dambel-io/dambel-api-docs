# `DELETE /api/v1/admin/equipment/{equipment-id}`
You can delete an equipment using this endpoint.


## Permissions
- `equipment.delete`: to delete any equipment

## Params

- `replacement_id`: In case the equipment you are deleting has some data attached to it, you transfer the data to another equipment by providing it's ID in this optional parameter

## Response

### 204 No Content
 No content when equipment gets deleted

### 400 Bad Request
 When equipment has data and `replacement_id` is not provided or is not valid. Number of the attached items is returned in `attached_data`.

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)

### 404 Not Found
 [Not-found error](../../not-found-errors.md)
