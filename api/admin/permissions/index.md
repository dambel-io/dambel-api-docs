# `GET /api/v1/admin/permissions`
You can get list of the permissions using this API.


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

[Permission Resource](../../resources/permission.md)
