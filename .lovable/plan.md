# Kennedy SaaS — UI gap review and build plan

Your repo is now copied into this project and compiles cleanly (21 screens, all assets,
the Caddy/Kennedy storefront, admin console and rider console).

I am ignoring the old Railway findings, as you asked. The truth I plan against is your
master guide: the upgraded backend (multi-tenant, 7 roles, phone-OTP, branches, sizes,
coupons, inventory, staff, billing, onboarding) exists — it just runs on your machine.

## One thing that shapes everything

Your backend is local, this app is online. An online page cannot reach `localhost`.
So every screen gets built against the real contract but runs on a switchable data
source: live API when a reachable URL is set, sample data otherwise. That way you can
review all screens today and flip one setting when the backend is exposed (public
tunnel or deployed). No screen will be written twice.

## What already exists vs what your upgraded backend offers

Built and usable: storefront home, dish page, cart, login/signup/password reset,
customer profile with orders + addresses + tracking, admin dashboard, orders list and
detail, riders, customers, payments, rider home/jobs/profile/earnings.

Built but out of date with the new backend:
- Cart/checkout: single price per dish, no size choice, no coupon field, no branch choice
- Login: password only, no phone-OTP, no forced password change, no tenant awareness
- Order status wording: screens still say "cooking"/"picking"; backend says kitchen/packed/onway
- Rider earnings screen runs on local data instead of the earnings figures
- Admin dashboard numbers assume exact field names and can break on a rename
- Three different visual styles across storefront, admin and rider

Not designed at all (whole product areas your backend now supports):
- Kitchen screen for the kitchen role
- Restaurant sign-up wizard (the thing that makes this a SaaS)
- Menu manager: dishes, categories, photos, discounts
- Inventory with low-stock warnings
- Staff manager with the one-time temporary password
- Branch manager and a branch picker for customers
- Billing: plan, trial countdown, invoices, payment proof upload
- Forced password change screen, and owner/manager/cashier roles

## Build order (chunks)

1. **Foundations** — restaurant (tenant) awareness on every request, the 7 roles and
   page permissions, one status vocabulary, prices parsed once, one live-refresh helper,
   forced password change. Mostly plumbing, little visible change.
2. **Customer flow upgrade** — phone + code sign-in with silent account creation, branch
   picker, dish sizes, multi-item cart, coupon box, checkout reading the real bill back
   from the order.
3. **Order tracking** — refreshing status timeline, rider map, rating dialog on delivery.
   Refresh by polling only; no realtime until you confirm it exists.
4. **Kitchen screen** — focused ticket board with one-tap status advance.
5. **Admin core** — orders feed with rider assignment, priority/ETA/notes, menu manager
   with photo upload and discounts.
6. **Owner tools** — inventory, staff, branches.
7. **SaaS layer** — sign-up wizard with trial, billing page, plans, invoice proof.
8. **Design unification** — one Caddy look across all three surfaces, keeping the
   storefront's animation personality.

## Technical notes

- Single HTTP door stays `src/lib/api/client.ts`: injects `X-Tenant-Slug`, bearer token,
  one silent refresh on 401, then redirect to login.
- Endpoint paths stay centralised in `src/lib/api/endpoints.ts`, updated to the new
  contract (`/api/orders/apply-coupon/`, `/api/rider/*`, `total` not `grand_total`).
- Unconfirmed fields (analytics, coupon path) read defensively with fallbacks so a wrong
  name shows zero instead of crashing.
- New route files per screen: `/change-password`, `/kitchen`, `/onboard`,
  `/admin/menu`, `/admin/inventory`, `/admin/staff`, `/admin/branches`, `/admin/billing`.
- One `useLiveResource(key, fetcher, interval)` hook replaces the scattered intervals, so
  swapping to sockets later is a single change.

Tell me which chunk to start with — I suggest 1 then 2.
