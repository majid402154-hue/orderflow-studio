# Next

## Now
Slice **2.1 Phone + code sign-in** — built (see `01-done.md`), awaiting your review.

## Queued (Phase 2 — Customer flow)
| Slice | What it adds | Notes |
|---|---|---|
| 2.2 Branch picker | Customer chooses the branch; `branch_id` rides along with the order | needs blocker **B4** |
| 2.3 Dish sizes | Size choice on the dish page and in the cart, price per size | safe to build with fallbacks |
| 2.4 Multi-item cart | Several dishes in one order | needs blocker **B1** |
| 2.5 Coupon box | Code applied at checkout, discount comes from the server | needs **B2** |
| 2.6 Real bill | Checkout shows subtotal / discount / delivery / total from the order response | needs **B1** |

Suggested order while B1 is open: **2.3 → 2.2 → 2.5 → 2.4 + 2.6** together once
multi-item is confirmed.

## After Phase 2
3 Order tracking (timeline, rider map, rating) · 4 Kitchen ticket board ·
5 Admin core (orders feed, controls, menu manager) · 6 Owner tools (inventory, staff,
branches) · 7 SaaS layer (sign-up wizard, billing, invoice proof) · 8 Design unification.
