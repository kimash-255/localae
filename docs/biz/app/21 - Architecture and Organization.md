# Architecture and Organization

This document defines the proposed app architecture and folder organization based on the UX flows, screen IDs, and feature definitions.

This is the structure we should confirm before updating the actual app.

## 1. Architecture Summary

| Principle | Decision |
| --- | --- |
| App style | Role-based at the top, feature-based within each role |
| Routing | `app/` stays thin and mostly wires routes to feature-owned screens |
| Business ownership | Lives in `src/features/*` |
| Shared systems | Live in `src/shared/*` |
| Reusable UI and infrastructure | Live in `src/shared` not scattered per screen |

## 2. Target High-Level Structure

```text
mobile-app/localae/
  app/
    (auth)/
    (customer)/
    (vendor)/
    (rider)/
    _layout.tsx
  src/
    features/
      auth/
      customer/
      vendor/
      rider/
    shared/
      api/
      navigation/
      transactions/
      ui/
      theme/
      notifications/
      wallet/
      support/
      profiles/
      ratings/
      settings/
      hooks/
      types/
      utils/
```

## 3. What `app/` Should Do

| `app/` Responsibility | Meaning |
| --- | --- |
| Define route groups | `(auth)`, `(customer)`, `(vendor)`, `(rider)` |
| Expose route entry files | Route files should point to feature-owned screens |
| Hold global layouts | Root navigation and route-group layouts |
| Avoid business logic | No heavy business state or API orchestration in route files |

## 4. What `src/features/` Should Do

| Area | Meaning |
| --- | --- |
| Own screen behavior | Feature screens should live with their own logic |
| Own feature-specific hooks and API calls | If it belongs to one feature, keep it there |
| Own feature types | Keep local types close if they are not shared |
| Own feature components | Reusable only within that feature unless promoted |

## 5. What `src/shared/` Should Do

| Shared Area | Meaning |
| --- | --- |
| Shared UI | Buttons, inputs, cards, layout primitives, loaders |
| Shared API | Base API client, request helpers, auth transport |
| Shared navigation | Route helpers, deep-link helpers, shell utilities |
| Shared transactions | Transaction lifecycle utilities and shared state coordination |
| Shared role-agnostic modules | Notifications, wallet, support, settings, profiles |
| Shared types | Common domain types used by multiple features |

## 6. Proposed Route Group Structure

```text
app/
  _layout.tsx
  (auth)/
    _layout.tsx
    login.tsx
    register.tsx
  (customer)/
    _layout.tsx
    home.tsx
    search-results.tsx
    product-detail.tsx
    service-detail.tsx
    events-feed.tsx
    event-detail.tsx
    vendor-map.tsx
    vendor-selection.tsx
    provider-list.tsx
    service-mode-selection.tsx
    payment-flow.tsx
    service-request.tsx
    participation.tsx
    event-marketplace.tsx
    orders/
      index.tsx
      [orderId].tsx
    order-tracking.tsx
    service-status.tsx
    event-tracking.tsx
  (vendor)/
    _layout.tsx
    dashboard.tsx
    analytics.tsx
    inventory/
      index.tsx
      add-product.tsx
      add-service.tsx
      [itemId].tsx
    inbox.tsx
    order-detail.tsx
    fulfillment-center.tsx
    events/
      index.tsx
      [eventId].tsx
      participation.tsx
  (rider)/
    _layout.tsx
    home.tsx
    availability.tsx
    job-feed.tsx
    job-detail.tsx
    accept-reject.tsx
    live-navigation.tsx
    delivery-tracking.tsx
    completion.tsx
    earnings/
      index.tsx
      withdrawals.tsx
      history.tsx
```

## 7. Proposed Feature Folder Structure

```text
src/features/
  auth/
    session/
    routing/
  customer/
    discovery/
    commerce/
    services/
    events/
    checkout/
    orders/
  vendor/
    operations/
    inventory/
    fulfillment/
    events/
    trust/
  rider/
    availability/
    jobs/
    delivery/
    earnings/
```

## 8. Proposed Shared Folder Structure

```text
src/shared/
  api/
  navigation/
  transactions/
  ui/
  theme/
  notifications/
  wallet/
  support/
  profiles/
  ratings/
  settings/
  hooks/
  lib/
  types/
  utils/
```

## 9. Feature-to-Folder Mapping

| Feature ID | Feature Name | Folder |
| --- | --- | --- |
| `F-G1` | Auth Session | `src/features/auth/session` |
| `F-G2` | Role Routing | `src/features/auth/routing` |
| `F-G3` | Global Navigation Context | `src/shared/navigation` |
| `F-G4` | Global Transaction Orchestration | `src/shared/transactions` |
| `F-C1` | Customer Discovery | `src/features/customer/discovery` |
| `F-C2` | Product Commerce | `src/features/customer/commerce` |
| `F-C3` | Service Booking | `src/features/customer/services` |
| `F-C4` | Event Discovery and Participation | `src/features/customer/events` |
| `F-C5` | Checkout and Payment | `src/features/customer/checkout` |
| `F-C6` | Customer Orders | `src/features/customer/orders` |
| `F-V1` | Vendor Operations | `src/features/vendor/operations` |
| `F-V2` | Vendor Inventory | `src/features/vendor/inventory` |
| `F-V3` | Vendor Fulfillment | `src/features/vendor/fulfillment` |
| `F-V4` | Vendor Events | `src/features/vendor/events` |
| `F-V5` | Vendor Trust | `src/features/vendor/trust` |
| `F-R1` | Rider Availability | `src/features/rider/availability` |
| `F-R2` | Rider Job Intake | `src/features/rider/jobs` |
| `F-R3` | Rider Delivery Execution | `src/features/rider/delivery` |
| `F-R4` | Rider Earnings | `src/features/rider/earnings` |
| `F-S1` | Notifications | `src/shared/notifications` |
| `F-S2` | Wallet and Ledger | `src/shared/wallet` |
| `F-S3` | Support | `src/shared/support` |
| `F-S4` | Identity and Profiles | `src/shared/profiles` |
| `F-S5` | Ratings and Trust Signals | `src/shared/ratings` |
| `F-S6` | Settings and Preferences | `src/shared/settings` |

## 10. Internal Feature Organization Pattern

Each feature can follow the same internal shape:

```text
src/features/customer/checkout/
  components/
  screens/
  hooks/
  api/
  types/
  utils/
```

Use only the folders the feature actually needs.

## 11. Promotion Rules

| If Something Is | Put It In |
| --- | --- |
| Used in only one feature | That feature folder |
| Used in multiple features of the same role | Role-level shared sub-area if needed later |
| Used across roles | `src/shared/*` |
| A route wrapper only | `app/*` |
| A reusable UI primitive | `src/shared/ui` |

## 12. Ownership Rules

| Rule | Meaning |
| --- | --- |
| Do not group by technical layer first | Avoid top-level `screens`, `components`, `services` buckets for the whole app |
| Do not let `shared` become a dump | Shared must mean cross-role and reusable |
| Keep route files thin | Route file imports a feature screen, not business logic trees |
| Keep screen ownership obvious | Each screen ID should map to one feature |
| Keep transaction logic centralized | Cross-role status and settlement logic should not be duplicated |

## 13. Suggested Build Order For Structure

| Step | What To Create |
| --- | --- |
| 1 | `app/` route groups and layouts |
| 2 | `src/features/auth`, `src/features/customer`, `src/features/vendor`, `src/features/rider` |
| 3 | `src/shared` foundations like `ui`, `api`, `navigation`, `types`, `theme` |
| 4 | Feature folders from `F-C1` through `F-R4` |
| 5 | Shared modules like wallet, notifications, support, settings |

## 14. Decision Summary

| Question | Answer |
| --- | --- |
| Is the architecture role-based? | Yes, at the top level |
| Is it feature-based? | Yes, inside each role |
| Is `shared` allowed? | Yes, but only for truly shared systems |
| Should `app/` own business logic? | No |
| Can we now update the real app structure after confirmation? | Yes |
