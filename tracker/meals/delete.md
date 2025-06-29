# `DELETE /api/v1/tracker/meals/{tracker-meal-id}`
You can delete a meal record in the tracker system using this API.


## Permissions

- `tracker_meals.delete`: deleting tracker meal

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
