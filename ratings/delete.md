# `DELETE /api/v1/ratings/{rating-id}`
You can delete a rating of any element using this API.


## Permissions

- You need to have **view** permission of the **ratable**
- `ratings.delete`: To delete your own ratings
- `ratings.delete_any`: To delete any rating

## Response

### 204 No Content
No content when rating gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
