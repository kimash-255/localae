# Feature Definitions

This document defines the app features and modules that will drive the architecture.

The goal is to decide:

1. what the real features are
2. what each feature owns
3. which screen IDs belong to each feature
4. which features are role-specific
5. which features belong in `shared`

After this, we can build the app structure from a clear feature map instead of guessing from screens alone.

## 1. Architecture Rule

| Principle | Meaning |
| --- | --- |
| Role-based at the top | Customer, vendor, and rider are the primary product boundaries |
| Feature-based inside each role | Each role area should be split into business capabilities, not loose screen folders |
| Shared stays truly shared | Cross-cutting systems belong in `shared`, not inside one role |
| Routing is thin | `app/` should mostly wire screens to features, not hold business logic |

## 2. Top-Level Feature Groups

| Group | Purpose | Target Location |
| --- | --- | --- |
| Global / Entry | Boot, auth, user-type routing, app shell setup | `src/features/auth` and routing layer |
| Customer Features | Discovery, purchase, service booking, events, order visibility | `src/features/customer/*` |
| Vendor Features | Operations, inventory, fulfillment, events, vendor trust | `src/features/vendor/*` |
| Rider Features | Availability, jobs, delivery, earnings | `src/features/rider/*` |
| Shared Features / Modules | Notifications, wallet, support, profiles, settings, shared transaction coordination | `src/shared/*` and limited shared feature modules |

## 3. Global / Entry Features

| Feature ID | Feature Name | Owns | Screen IDs | Why It Exists |
| --- | --- | --- | --- | --- |
| F-G1 | Auth Session | Splash boot, login, register, session restore | `G1`, `G2`, `G3` | Entry and authentication lifecycle |
| F-G2 | Role Routing | User-type based routing and shell handoff | `G4`, `G5` | Send the user into the correct app shell |
| F-G3 | Global Navigation Context | Deep links, route handoff, shell readiness | `G5`, `G7` | Connect app-wide routing behavior |
| F-G4 | Global Transaction Orchestration | Cross-role transaction lifecycle coordination | `G6` | Keep the same transaction visible across actors |

## 4. Customer Features

| Feature ID | Feature Name | Owns | Screen IDs | Why It Exists |
| --- | --- | --- | --- | --- |
| F-C1 | Customer Discovery | Browse, search, and customer entry discovery | `C1`, `C2` | Start demand creation |
| F-C2 | Product Commerce | Product evaluation and seller choice for goods | `C3`, `C7`, `C8` | Convert product demand into a purchasable order |
| F-C3 | Service Booking | Service evaluation, provider choice, and request submission | `C4`, `C9`, `C10`, `C12`, `C18` | Convert service demand into a managed booking |
| F-C4 | Event Discovery and Participation | Event browsing, event details, participation, event marketplace | `C5`, `C6`, `C13`, `C14`, `C19` | Turn urgency and event engagement into activity and purchases |
| F-C5 | Checkout and Payment | Order totals, payment confirmation, transaction start | `C11` | Create the transaction record cleanly |
| F-C6 | Customer Orders | Order list, detail, and tracking | `C15`, `C16`, `C17` | Give post-purchase visibility |

## 5. Vendor Features

| Feature ID | Feature Name | Owns | Screen IDs | Why It Exists |
| --- | --- | --- | --- | --- |
| F-V1 | Vendor Operations | Dashboard and analytics | `V1`, `V2` | Help vendors understand business state |
| F-V2 | Vendor Inventory | Product and service listing management | `V3`, `V4`, `V5`, `V6` | Keep supply current and structured |
| F-V3 | Vendor Fulfillment | Inbox, request detail, fulfillment center | `V7`, `V8`, `V9` | Turn requests into completed work |
| F-V4 | Vendor Events | Event opportunity evaluation and participation | `V10`, `V11`, `V12` | Support demand spikes and event commerce |
| F-V5 | Vendor Trust | Vendor profile and vendor-side reputation | `V13`, `V14` | Build confidence and business visibility |

## 6. Rider Features

| Feature ID | Feature Name | Owns | Screen IDs | Why It Exists |
| --- | --- | --- | --- | --- |
| F-R1 | Rider Availability | Rider readiness and online or offline state | `R1`, `R2` | Control whether a rider can receive work |
| F-R2 | Rider Job Intake | Job feed, job detail, accept or reject | `R3`, `R4`, `R5` | Help riders decide on assignments fast |
| F-R3 | Rider Delivery Execution | Live navigation, progress tracking, completion | `R6`, `R7`, `R8` | Execute the physical part of the transaction |
| F-R4 | Rider Earnings | Earnings snapshot, withdrawals, earnings history | `R9`, `R10`, `R11` | Close the rider work-to-money loop |

## 7. Shared Features / Modules

| Feature ID | Feature Name | Owns | Screen IDs | Why It Exists |
| --- | --- | --- | --- | --- |
| F-S1 | Notifications | User alerts and notification feed | `S1` | Shared communication layer across all roles |
| F-S2 | Wallet and Ledger | Wallet home, history, payment methods, wallet modal | `S2`, `S3`, `S4`, `S5` | Shared money visibility and financial actions |
| F-S3 | Support | Support flows and issue context | `S6` | Recovery path when something goes wrong |
| F-S4 | Identity and Profiles | Customer, vendor, rider profile views | `S7`, `S8`, `S9` | Shared identity presentation layer |
| F-S5 | Ratings and Trust Signals | Reputation display and review summary | `S10` | Trust visibility after transactions |
| F-S6 | Settings and Preferences | Customer, vendor, rider, and global settings | `S11`, `S12`, `S13`, `S14` | Shared preference and account control system |

## 8. Proposed Folder Mapping

| Feature ID | Proposed Folder |
| --- | --- |
| F-G1 | `src/features/auth/session` |
| F-G2 | `src/features/auth/routing` |
| F-G3 | `src/shared/navigation` |
| F-G4 | `src/shared/transactions` |
| F-C1 | `src/features/customer/discovery` |
| F-C2 | `src/features/customer/commerce` |
| F-C3 | `src/features/customer/services` |
| F-C4 | `src/features/customer/events` |
| F-C5 | `src/features/customer/checkout` |
| F-C6 | `src/features/customer/orders` |
| F-V1 | `src/features/vendor/operations` |
| F-V2 | `src/features/vendor/inventory` |
| F-V3 | `src/features/vendor/fulfillment` |
| F-V4 | `src/features/vendor/events` |
| F-V5 | `src/features/vendor/trust` |
| F-R1 | `src/features/rider/availability` |
| F-R2 | `src/features/rider/jobs` |
| F-R3 | `src/features/rider/delivery` |
| F-R4 | `src/features/rider/earnings` |
| F-S1 | `src/shared/notifications` |
| F-S2 | `src/shared/wallet` |
| F-S3 | `src/shared/support` |
| F-S4 | `src/shared/profiles` |
| F-S5 | `src/shared/ratings` |
| F-S6 | `src/shared/settings` |

## 9. Feature Dependencies

| Feature | Depends On | Reason |
| --- | --- | --- |
| F-G1 Auth Session | shared API, storage, validation | Sign-in and restore state |
| F-G2 Role Routing | F-G1, shared navigation | Route after auth |
| F-C1 Customer Discovery | shared API, location, shared UI | Load and show marketplace demand paths |
| F-C2 Product Commerce | F-C1, F-S4, F-C5 | Product choice leads into trust and payment |
| F-C3 Service Booking | F-C1, F-S4 | Provider comparison and request flow |
| F-C4 Events | F-C1, F-C5 | Event engagement can lead to purchases |
| F-C5 Checkout | F-S2, F-G4 | Payment must create a transaction record |
| F-C6 Customer Orders | F-G4, F-S1 | Order state relies on notifications and transaction updates |
| F-V3 Vendor Fulfillment | F-G4, F-S1, F-R2 | Vendor execution may trigger rider assignment |
| F-R2 Rider Job Intake | F-G4 | Jobs are derived from active transactions |
| F-R3 Rider Delivery Execution | F-R2, F-S1 | Delivery updates must flow back into the system |
| F-S2 Wallet and Ledger | F-G4 | Financial state depends on transaction lifecycle |

## 10. What Is Not A Feature

These should not become top-level business features:

| Not a Feature | Why |
| --- | --- |
| `screens` | A screen is just a UI entry point, not an ownership boundary |
| `components` | Components are building blocks, not business capabilities |
| `hooks` | Hooks are implementation tools, not product domains |
| `services` | Too broad and becomes a dumping ground |
| `utils` | Generic helper area, not business architecture |

## 11. Feature Definition Rules

| Rule | Meaning |
| --- | --- |
| A feature must own behavior, not just UI | It should represent a business capability |
| A feature should have a clear entry and exit | It must connect meaningfully to the UX flow |
| A feature should map to one or more screen IDs | This keeps planning and code aligned |
| Shared modules should not absorb role logic | If it is role-specific, keep it in that role |
| If a feature grows too large, split it by capability | Example: customer discovery vs customer checkout |

## 12. Final Feature Set For Architecture

This is the recommended feature set to use when creating the app structure:

| Area | Features |
| --- | --- |
| Global / Entry | F-G1, F-G2, F-G3, F-G4 |
| Customer | F-C1, F-C2, F-C3, F-C4, F-C5, F-C6 |
| Vendor | F-V1, F-V2, F-V3, F-V4, F-V5 |
| Rider | F-R1, F-R2, F-R3, F-R4 |
| Shared | F-S1, F-S2, F-S3, F-S4, F-S5, F-S6 |

## 13. What This Enables Next

Once this feature definition is accepted, the next step is to create:

1. the route group structure in `app/`
2. the feature folders in `src/features/`
3. the cross-cutting folders in `src/shared/`
4. thin route files that point into feature-owned screens
