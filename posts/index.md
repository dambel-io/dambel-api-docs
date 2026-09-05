# GET /api/v1/posts

Retrieves a list of posts, with support for filtering by profile type, profile ID, search, and order.


---

## Permissions
| Permission       | Description                                                  |
|------------------|--------------------------------------------------------------|
| `posts.view`     | View your own posts and posts on any public profile          |
| `posts.view_all` | View all posts, including drafts, on any profile (admin only)|

---

## Query Parameters
| Name    | Type   | Required | Description                                                                          | Example                               |
|---------|--------|----------|--------------------------------------------------------------------------------------|---------------------------------------|
| type    | string | No       | Profile type (`App\Models\Gym`, `App\Models\User`). Comma-separated for multiple    | "App\\Models\\Gym,App\\Models\\User" |
| item_id | int    | No       | Profile ID(s) to filter by (comma-separated for multiple)                            | "1,2,3"                               |
| in_blog | bool   | No       | Filter posts by blog publication status (`true` for blog posts, `false` for regular posts) | "true"                         |
| search  | string | No       | Search term for post title or content. Max 255 characters. Persian-normalized — see the note below. | "workout"                             |
| order   | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                                 | "DESC"                                |

> **`search` matching.** The term and the text it is matched against are both normalized first, so
> a post written with an Arabic keyboard's `ي`/`ك` is found by a search typed with the Persian
> `ی`/`ک` and vice versa; the same applies to hamza-bearing alefs, teh marbuta, zero-width joiners
> and non-joiners, the tatweel, Arabic diacritics, and Persian or Arabic-Indic digits (`۲۴` and
> `24` match each other). Title and body are both matched, case-insensitively and anywhere in the
> text. **`%` and `_` are literal characters** — `?search=%` returns only posts whose text actually
> contains a percent sign, not every post. A term that normalizes to nothing (whitespace alone) is
> treated as no filter at all.

---

## Response

### 200 OK
Returns a paginated list of post resources.

```json
{
  "data": [
    {
      "id": 123,
      "profile_type": "App\\Models\\User",
      "profile_id": 42,
      "title": "My Workout",
      "content": "Today I did squats and deadlifts.",
      "is_draft": false,
      "media": [
        {
          "id": 10,
          "attachable_type": "App\\Models\\Posts\\Post",
          "attachable_id": 123,
          "link": "https://example.com/media/10.jpg"
        }
      ]
    }
  ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

See [Post Resource](post_resource.md) and [Pagination Data](../_globals/pagination-data.md) (per page: 30).

---

### Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../_globals/not-found-errors.md)           |
| 422    | Validation error — `search` exceeded 255 characters | [Validation error](../_globals/validation-errors.md) |
