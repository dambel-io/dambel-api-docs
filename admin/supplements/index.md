# `GET /api/v1/admin/supplements`
You can get list of the supplements using this endpoint.


## Permissions

- `supplements.view_all`: to access supplements

## Response

### 200 OK

```json
{
    "data": [
        {<supplement resource>},
        {<supplement resource>},
        {<supplement resource>},
        {<supplement resource>}
    ],
}
```

[Supplement Resource](supplement_resource.md)
