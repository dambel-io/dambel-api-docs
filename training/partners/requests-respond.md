# PUT /api/v1/training/partners/requests/{request-id}

Answer a training-partner request. **Only the addressee may answer.**


---

## Permissions
| Permission                  | Description               |
|-----------------------------|---------------------------|
| `training_partners.respond` | Answer a partner request  |

The requester is refused with **403**, as is any other user. This is where the feature's mutual
consent actually lives: the person who asked cannot answer on behalf of the person asked.

---

## Path Parameters
| Name         | Type | Description        |
|--------------|------|--------------------|
| `request-id` | int  | The request to answer |

---

## Request Body
| Name     | Type   | Required | Description               |
|----------|--------|----------|---------------------------|
| `status` | string | Yes      | `accepted` or `declined`  |

`pending` is not an answer and is not accepted. **A request can be answered once**: a second answer
is a 422 on `status`. Without that, accepting and then declining would leave a live chat behind a
request that reads `declined`.

---

## What acceptance does

Accepting opens a [chat](../../chats/index.md) containing exactly the two users and stores its id on
the request, inside the same transaction as the status change — so acceptance has a concrete
outcome rather than only flipping a flag. The requester is told through the existing
`YouAreAddedToChatNotification`; this feature introduces **no new notification type**.

Declining creates no chat and notifies nobody.

**The honest limitation:** `POST /api/v1/chats` remains open to any user id platform-wide. This
consent gate constrains *this feature's* flow — a match does not become a conversation until both
sides agree — not the chat API in general. Closing that is a separate change.

---

## Response

### 200 OK
```json
{
  "data": <training partner request resource>
}
```
- See [Training Partner Request Resource](training_partner_request_resource.md)

---

## Error Responses
| Status | Error Type       | Reference                                                       |
|--------|------------------|-----------------------------------------------------------------|
| 401    | Unauthorized     | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden        | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found        | [Not found error](../../_globals/not-found-errors.md)           |
| 422    | Validation Error | [Validation error](../../_globals/validation-errors.md)         |

---
