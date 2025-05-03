# `DELETE /api/v1/admin/countries/{country-id}`
You can delete a country using this endpoint.


## Permissions

- `countries.view_all`: to access countries
- `countries.delete`: to delete any country

## Params

- `replacement_id`: In case the country you are deleting has some data attached to it, you transfer the data to another country by providing it's ID in this optional parameter

## Response

### 204 No Content
 No content when country gets deleted

### 400 Bad Request
 When country has data and `replacement_id` is not provided or is not valid. Number of attached items are returned in `attached_data`.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
