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
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
