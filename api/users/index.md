# `GET /api/v1/users`
Using this API you can get list of the users and also search them using filters.


### Permissions

- `users.view_any`: to view all of the users

### Params

- `page`: page number
- `search`: search by a text in user's name, email, and phone
- `email_status`: can be `verified` or `not_verified`
- `phone_status`: can be `verified` or `not_verified`
- `user_id`: only return one or more specific ids
- `sort_by`: can be `name`, `email`, `phone`, `created_at`, `email_verified_at`, `phone_verified_at` (default sort is `created_at`)
- `sort_order`: can be `desc` or `asc` (default order is `desc`)

The users are sorted by the newest.

### Response

200:
```json
{
    "data": [
        {<user resource>},
        {<user resource>},
        {<user resource>},
        {<user resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[User Resource](../resources/user.md)

[Pagination Data](../pagination-data.md) (per page: 30)
