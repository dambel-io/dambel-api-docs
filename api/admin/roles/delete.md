# `/api/v1/admin/roles/{role-id}`
You can delete a role using this endpoint.

- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `roles.delete`: to delete any role

### Response

204: No content when state gets deleted

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
