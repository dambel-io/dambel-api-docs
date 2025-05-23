# `POST /api/v1/media`
You can attach an media to an element using this API.


## Permissions
You need to have **update** permission of the **attachable**.

## Params

- `attachable_type`: Type of the element that you are attaching the media to. These are available items:
  - `championship`
  - `gym`
  - `gym_equipment`
  - `post`
  - `user`
  - `education`
  - `gym_buffet_item`
  - `training_service`
- `attachable_id`: Id of the element
- `file`: The media file

## Response

### 201 Created
```json
{
    "media": {<media resource>},
}
```

[Media Resource](media_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
