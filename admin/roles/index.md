# `GET /api/v1/admin/roles`
You can get list of the roles using this API.


## Permissions

- `roles.view_all`: to access roles

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

[Role Resource](role_resource.md)
