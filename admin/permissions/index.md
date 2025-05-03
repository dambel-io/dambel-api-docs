# `GET /api/v1/admin/permissions`
You can get list of the permissions using this API.


## Permissions

- `permissions.view_any`: to access permissions

## Response

### 200 OK

```json
{
    "data": [
        {<permission resource>},
        {<permission resource>},
        {<permission resource>},
        {<permission resource>}
    ],
}
```

[Permission Resource](permission_resource.md)
