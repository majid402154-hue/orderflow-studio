# Kennedy Frontend — Phase & Slice Roadmap

Review after every slice, then continue to the next.

## Phase 1 — Foundations
- [x] 1.1 Tenant awareness: X-Tenant-Slug on every request from a global context
- [x] 1.2 7 roles + page permission guards
- [x] 1.3 Unified status vocabulary (kitchen/packed/onway replaces cooking/picking)
- [x] 1.4 Single price parser + forced password-change screen
- [x] 1.5 useLiveResource(key, fetcher, interval) hook replacing scattered intervals
- [x] 1.6 Fix ConnectionBanner double /api/api/menu/ bug; admin.riders.tsx hardcoded paths -> endpoints.ts

## Phase 2 — Customer Flow Upgrade
BLOCKER: confirm backend accepts multi-item `items: []` before starting (test order).
- [x] 2.1 Phone+code sign-in, silent account creation (details in /roadmap folder)
- [ ] 2.2 Branch picker
- [ ] 2.3 Dish size selection
- [ ] 2.4 Multi-item cart
- [ ] 2.5 Coupon box
- [ ] 2.6 Checkout shows real bill from order response

## Phase 3 — Order Tracking
- [ ] 3.1 Polling status timeline
- [ ] 3.2 Rider live map
- [ ] 3.3 Rating dialog on delivery

## Phase 4 — Kitchen Screen
- [ ] 4.1 3-column ticket board
- [ ] 4.2 One-tap status advance
- [ ] 4.3 New-order audio alert

## Phase 5 — Admin Core
- [ ] 5.1 Orders feed + rider assignment
- [ ] 5.2 Priority/ETA/notes controls
- [ ] 5.3 Fix unassign rider (real call) + proper refund flow (confirm endpoint with backend)
- [ ] 5.4 Menu manager: dishes, categories, photo upload, discounts

## Phase 6 — Owner Tools
- [ ] 6.1 Inventory + low-stock warnings
- [ ] 6.2 Staff manager via POST /api/admin/staff/ (not /api/admin/riders/), show one-time temp password
- [ ] 6.3 Branch manager + customer branch picker + plan quota 403 UI with billing link

## Phase 7 — SaaS Layer
- [ ] 7.1 Restaurant sign-up wizard with trial
- [ ] 7.2 Billing page: plan + trial countdown
- [ ] 7.3 Invoice proof upload

## Phase 8 — Design Unification
- [ ] 8.1 One Caddy token system across storefront/admin/rider (keep storefront motion)
