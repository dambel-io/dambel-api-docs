# `GET /api/v1/admin/majors`
You can get list of the majors using this endpoint.


## Permissions

- `majors.view_all`: to access majors

## Response

### 200 OK

```json
{
    "data": [
        {<major resource>},
        {<major resource>},
        {<major resource>},
        {<major resource>}
    ],
}
```

[Major Resource](major_resource.md)
