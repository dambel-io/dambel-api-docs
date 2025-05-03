# `GET /api/v1/admin/brands`
You can get list of the brands by alphabetical order using this endpoint.


## Permissions

- `brands.view_all`: to access brands

## Response

### 200 OK

```json
{
    "data": [
        {<brand resource>},
        {<brand resource>},
        {<brand resource>},
        {<brand resource>}
    ],
}
```

[Brand Resource](brand_resource.md)
