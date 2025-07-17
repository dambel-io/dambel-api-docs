# Gym Buffet Item Resource

Represents a buffet item available at a gym, including pricing, discount, and media.


---

## Schema
| Field            | Type         | Description                                 |
|------------------|--------------|---------------------------------------------|
| id               | int          | Unique identifier for the buffet item       |
| gym_id           | int          | ID of the gym                               |
| title            | string       | Title of the buffet item                    |
| description      | string       | Description of the buffet item              |
| price            | int          | Price of the item                           |
| discount         | float        | Discount percentage                         |
| discounted_price | float        | Price after discount                        |
| media            | array        | List of media resources                     |

---

## Example
```json
{
  "id": 1,
  "gym_id": 123,
  "title": "Protein Bar",
  "description": "Tasty bar",
  "price": 100,
  "discount": 10.5,
  "discounted_price": 89.5,
  "media": []
}
```

For media schema, see [Media Resource](../../media/media_resource.md).
