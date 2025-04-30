# `GET /api/v1/admin/roles`
You can get list of the roles using this API.


## Permissions
- `roles.view_any`: to update your own gym

## Response

### 200 OK

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

[Role Resource](role.md)
