# GET /api/v1/payments/prices

Retrieves general data for premium plan prices, commission rates, boost plans and the payment
gateway's fee. The response is the whole `config/monetization.php` array, so anything added there
appears here. All prices are in Tooman.


**No authentication required.**

---

## Response

### 200 OK
Returns platform pricing and commission data.

#### Example
`gateway_fee` describes what the payment gateway charges the user on top of a deposit — see
[the gateway fee](../../payments.md#currency-and-the-gateway-fee) for the formula. Clients do not
need to compute it: [`POST /payments/deposit`](deposit.md) returns the resolved figures.

`vat_rate` is the VAT Dambel adds to what it charges for itself — a Premium subscription, a
marketing boost, and the platform commission on a sale. It is a decimal fraction (`0.09` is 9%)
and is `0` in every environment until an operator sets it, so a client rendering prices today sees
no change. **It is not `gateway_fee.tax_rate`**, which is Zibal's tax on Zibal's own fee for
processing a deposit. See [commission](../../payments.md#commission).

```json
{
  "gym_commission_rate": 0.01,
  "vat_rate": 0,
  "gateway_fee": {
    "rate": 0.01,
    "min": 2000,
    "max": 20000,
    "tax_rate": 0.1
  },
  "premium_plans": {
    "plus": {
      "monthly_price": 1999000,
      "discount": 0,
      "yearly_price_discount": 0.85,
      "role": "user_plus"
    }
  },
  "boosts": {
    "basic": {
      "price": 99000,
      "duration": 7,
      "level": 1
    },
    "pro": {
      "price": 190000,
      "duration": 14,
      "level": 2
    }
  }
}
```
