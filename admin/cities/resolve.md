# GET /api/v1/admin/cities/resolve

Resolve a map pin to the nearest known city, with its state and country. The app calls this under the gym form's
map so the user sees "Tehran, Tehran, Iran" before saving. The same resolver derives a gym's `city_id` on
[`POST /api/v1/gyms`](../../gyms/create.md) and [`PUT /api/v1/gyms/{gym-id}`](../../gyms/update.md), so the city
previewed here is the city a save will store.


**Authentication required.** Any signed-in user may call it, because cities are public reference data.
**Rate limited:** 60 requests per minute (`throttle:60,1`). Debounce pin moves on the client.

---

## Query Parameters
| Name           | Type   | Required | Description                         |
|----------------|--------|----------|-------------------------------------|
| `location_lat` | number | Yes      | Pin latitude, between `-90` and `90` |
| `location_lng` | number | Yes      | Pin longitude, between `-180` and `180` |

---

## How a pin is resolved

- Each city may carry its centre coordinates, seeded from platform data. Cities without coordinates are never picked.
- The city whose centre is **nearest** to the pin wins, provided it is within **100 km**. Beyond that, the pin is
  rejected with the `location` error below.
- This is nearest-centre, not boundary containment, so it is approximate near city borders. In particular, master
  data lists several Tehran neighbourhoods as separate cities in Tehran province, so a pin in north Tehran may resolve
  to "Tajrish" and one in the south to "Shahr-e-Rey" rather than "Tehran". The state and country are unaffected.

---

## Response

### 200 OK
```json
{
  "data": {<city resource>}
}
```
- [City Resource](city_resource.md), with `state` and `state.country` nested. Its `location_lat` / `location_lng` are
  the resolved city's own centre, not the pin that was sent.

---

### 422 Unprocessable Entity — no city near the pin
```json
{
  "errors": {
    "location": ["We couldn't find a city near this location. Move the pin closer to a town, or choose the city manually."]
  }
}
```

The `location` key is the stable, machine-readable code: no other validation rule emits it. The message is localized.
Gym create and update return this same error for the same pin.

Missing, non-numeric or out-of-range coordinates return the standard [validation errors](../../_globals/validation-errors.md)
on `location_lat` / `location_lng`.

---

### 401 Unauthorized
- [Authentication Errors](../../_globals/authentication-errors.md)

### 429 Too Many Requests
- [Rate Limit Errors](../../_globals/rate-limit-errors.md)

---

## Related Resources
- [`GET /api/v1/admin/cities`](index.md)
- [`POST /api/v1/gyms`](../../gyms/create.md)
- [`PUT /api/v1/gyms/{gym-id}`](../../gyms/update.md)
