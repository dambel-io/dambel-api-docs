# `/api/v1/gyms/{gym-id}/working-periods/{working-period-id}`
You can delete a working period from a gym using this API.

- Controller: [`App\Http\Controllers\API\V1\Gyms\WorkingPeriods\DeleteWorkingPeriodController`](../../../../src/app/Http/Controllers/API/V1/Gyms/WorkingPeriods\DeleteWorkingPeriodController.php)
- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_working_periods.delete`: deleting working periods from their own gyms
- `gym_working_periods.delete_any`: deleting working period of any gym

### Params

No parameter.

### Response

204: No content when working period gets deleted

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
