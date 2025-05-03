# `GET /api/v1/admin/exercises`
You can get list of the exercises by alphabetical order using this endpoint.


## Permissions

- `exercises.view_all`: to access exercises

## Response

### 200 OK

```json
{
    "data": [
        {<exercise resource>},
        {<exercise resource>},
        {<exercise resource>},
        {<exercise resource>}
    ],
}
```

[Exercise Resource](exercise_resource.md)
