# GET /api/v1/posts/blog

Retrieves a list of posts, with support for filtering by profile type, profile ID, search, and order. This endpoint is used to retrieve blog posts for the website.


**No authentication required.**

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example                |
|-----------|--------|----------|-----------------------------------------------------------------------------|------------------------|
| search    | string | No       | Search term for post title or content. Max 255 characters. Persian-normalized — see the note below. | "workout"             |
| ids    | string | No       | Get specific posts by ID(s)                                       | "1,2"             |
| order     | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |
| per_page     | int | No       | Set the per page count (default: 50)                         | 10                 |

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

#### Schema
```json
{
  "data": [
    { /* Post Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

### 422 Unprocessable Entity
`per_page` was outside 1–100, or `search` exceeded 255 characters. See [Validation error](../_globals/validation-errors.md).

For a full schema, see [Post Resource](post_resource.md) and [Pagination Data](../_globals/pagination-data.md).
