# Training Service Resource

Represents a training service offered by a user.


---

## Schema
| Field              | Type    | Description                                 |
|--------------------|---------|---------------------------------------------|
| `id`               | integer | Training service ID                         |
| `user_id`          | integer | User ID who offers the service              |
| `title`            | string  | Title of the training service               |
| `description`      | string  | Description                                 |
| `price`            | integer | Price of the training service               |
| `discount`         | float   | Discount percentage                         |
| `discounted_price` | integer | Price after discount                        |
| `media`            | array   | List of [Media Resource](../../media/media_resource.md) |
| `rating_count`     | integer | Number of ratings                           |
| `rating_average`   | float   | Average rating                              |
| `boost`            | object/null | [Marketing Boost Resource](../../payments/marketing_boost_resource.md) |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "title": "...",
  "description": "...",
  "price": 123,
  "discount": 0,
  "discounted_price": 123,
  "media": [<media resource>, ...],
  "rating_count": 123,
  "rating_average": 4.5,
  "boost": null
}
```

---
