# Open blockers (only the backend/owner can clear these)

| # | Question | Blocks | Status |
|---|---|---|---|
| B1 | Does `POST /api/orders/` accept a multi-item `items: [{dish_id, size_id, qty}]` array? | Slices 2.4, 2.6 (checkout would 400) | **OPEN** |
| B2 | Is the coupon path `/api/orders/apply-coupon/`? | 2.5 | Assumed, coded defensively |
| B3 | Do `/api/auth/phone-otp/` and `/api/auth/phone-verify/` exist on the deployed host? | 2.1 goes live | Coded, degrades gracefully |
| B4 | Does `/api/branches/` exist and return branches per tenant? | 2.2, 6.3 | OPEN |
| B5 | Exact analytics field names (`avg_order_value` vs `average_order_value`)? | 5.x dashboard | Fallbacks in place |
| B6 | Dedicated refund endpoint (today the UI works around verify-payment) | 5.3 | OPEN |
| B7 | Is `/api/rider/earnings/` live on the deployed host? | rider earnings screen | 404 on old host |

Coding continues around every blocker: the screen is built, and where the endpoint is
missing it falls back to sample data plus a clear notice instead of an error.
