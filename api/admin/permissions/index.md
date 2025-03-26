# `/api/v1/admin/permissions`
You can get list of the permissions using this API.

- Method: `GET`

### Response

200:
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
