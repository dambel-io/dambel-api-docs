# GET /api/v1/admin/service-health

Lists the third-party services that are currently failing, with how long each has been broken and how many times
it has failed. An empty list is the healthy answer.

Nothing on this platform pages anyone. SMS.ir running out of credit, an OpenAI key with an exhausted quota and a
Google Custom Search key with the API disabled all fail the same way: a user-facing action 500s, a line goes into a
log nobody is watching, and the platform looks broken for hours. This endpoint is where an operator finds out.


---

## Permissions
| Permission                 | Description                                     |
|----------------------------|-------------------------------------------------|
| `service_health.view_all`  | Read the third-party outage dashboard           |

Held by `super_admin` and `operator`. It is its own permission rather than riding on an existing operator one, so
a dashboard client can be granted it without anything else.

---

## Query Parameters
None. The list is at most one row per provider (`smsir`, `openai`, `google_search`) and does not paginate.

---

## Response

### 200 OK
Returns the providers currently in a failed state, `critical` first and then most recently seen.

#### Example
```json
{
  "data": [
    {
      "provider": "openai",
      "severity": "critical",
      "reason": "credit_exhausted",
      "code": "insufficient_quota",
      "detail": "You exceeded your current quota",
      "first_seen_at": "2026-08-31 10:00:00",
      "last_seen_at": "2026-08-31 11:42:07",
      "failure_count": 128
    }
  ]
}
```

| Field           | Type          | Description                                                                    |
|-----------------|---------------|--------------------------------------------------------------------------------|
| `provider`      | string        | `smsir`, `openai` or `google_search`                                           |
| `severity`      | string        | `critical` when the account is out of money or quota, otherwise `warning`      |
| `reason`        | string        | See the table below                                                            |
| `code`          | string\|null  | The provider's own error code, or the HTTP status when it gave none            |
| `detail`        | string\|null  | The provider's own message, or an exception class for a transport failure      |
| `first_seen_at` | string (date) | When this outage started                                                       |
| `last_seen_at`  | string (date) | The most recent failure                                                        |
| `failure_count` | integer       | Failures since `first_seen_at`                                                 |

| `reason`            | Meaning                                                                          |
|---------------------|----------------------------------------------------------------------------------|
| `credit_exhausted`  | Out of money or quota. Will not resolve on its own — **the only `critical` one** |
| `rate_limited`      | Too many requests. Resolves on its own                                           |
| `rejected`          | SMS.ir declined the request; read `detail` for why                               |
| `transport`         | The provider could not be reached at all                                         |
| `forbidden`         | Google Custom Search returned 403 — usually a disabled API or a restricted key   |
| `error`             | Anything else                                                                    |

**An empty `data` array means nothing is broken.** The response never lists healthy providers.

**This is a live view, not an audit trail.** Entries live in the cache, expire 24 hours after the *last* failure,
and are deleted the moment the same provider succeeds — so a provider that recovers drops off the list on its next
successful call. The logs remain the record of what happened; this is the answer to "is it broken right now".

`detail` carries the provider's own message and never our request, so it contains no phone number, OTP code or API
key. A transport failure records only the exception class, because such a message can carry the request URI. As a
backstop, `ServiceHealth::recordFailure()` masks phone-, key- and IBAN-shaped substrings to `[redacted]` before
storing, so a careless future caller degrades rather than putting a secret on this dashboard.

---

### Error Responses
| Status | Description                                        | Reference                                                       |
|--------|----------------------------------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized (not authenticated)                   | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (missing `service_health.view_all`)      | [Permission error](../../_globals/permission-errors.md)         |

---

## Related Resources
- [SMS](../../../sms.md) — the SMS.ir integration and its error handling
- [AI](../../../ai.md) — the OpenAI transport and the `searchWeb` tool
- [Permissions](../../../permissions.md)
