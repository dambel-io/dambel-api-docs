# `/api/v1/admin/roles`
You can get list of the roles using this API.

- Method: `GET`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `roles.view_any`: to update your own gym

### Response

200:
```json
{
    "data": [
        {<role resource>},
        {<role resource>},
        {<role resource>},
        {<role resource>}
    ],
}
```

[Role Resource](../../resources/role.md)
