# DELETE /api/v1/tracker/shares/{shared-tracker-id}

Delete an existing shared tracker configuration.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `shared_trackers.delete`   | Delete shared tracker      |
| `shared_trackers.view`     | View shared tracker        |

---

## URL Parameters
| Name            | Type    | Required | Description                    |
|-----------------|---------|----------|--------------------------------|
| `sharedTracker` | integer | Yes      | ID of the shared tracker to delete |

---

## Response

### 204 No Content
Shared tracker deleted.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---

## Notes

- Users can only delete shared trackers where they are either the owner (`user_id`) or the viewer (`viewer_user_id`)
- The deletion is permanent and cannot be undone
- All associated data and configurations will be removed
