# `DELETE /api/v1/gyms/{gym-id}`
You can delete a gym using this API (as normal user deleting their own gym and also admin user being able to delete all gyms).


## Permissions
- `gyms.delete`: to delete your own gym
- `gyms.delete_any`: to delete someone else's gym

## Params

- `id`: ID of the gym in the route

## Response

### 204 No Content
 No content when gyms gets deleted

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
