# ID Key and Naming Conventions

This document defines how IDs are used across screens, flows, and features so every planning and architecture document stays consistent.

## 1. Why This Exists

| Need | Meaning |
| --- | --- |
| Clear cross-reference | A screen, feature, or module should be easy to find everywhere |
| Consistent naming | The same thing should not have multiple labels in different docs |
| Cleaner architecture work | Folder names and route groups should come from stable definitions |

## 2. ID Families

| ID Family | Meaning | Example |
| --- | --- | --- |
| `G#` | Global / entry screens and modules | `G1`, `G4` |
| `S#` | Shared screens and shared reusable user-facing modules | `S1`, `S6` |
| `C#` | Customer screens | `C1`, `C11` |
| `V#` | Vendor screens | `V1`, `V9` |
| `R#` | Rider screens | `R1`, `R8` |
| `SM#` | Shared internal modules | `SM1`, `SM5` |
| `F-G#` | Global features | `F-G1` |
| `F-C#` | Customer features | `F-C4` |
| `F-V#` | Vendor features | `F-V3` |
| `F-R#` | Rider features | `F-R2` |
| `F-S#` | Shared features | `F-S2` |

## 3. Screen ID Definitions

### 3.1 Global IDs

| ID | Name | Definition |
| --- | --- | --- |
| `G1` | Splash Screen | Boot screen that restores session state and app readiness |
| `G2` | Login Screen | Existing-user sign-in screen |
| `G3` | Register Screen | New-user account creation screen that also persists user type |
| `G4` | Role Router | Logic entry that reads stored user type and opens the correct shell |
| `G5` | App Shell Loader | Role-shell bootstrap and navigation readiness layer |
| `G6` | Global Transaction State | Shared transaction lifecycle coordination module |
| `G7` | Global Deep Link Resolver | Shared route resolution for links and notification targets |

### 3.2 Shared IDs

| ID | Name | Definition |
| --- | --- | --- |
| `S1` | Notifications Screen | Shared alert feed and notification entry surface |
| `S2` | Wallet Home Screen | Shared wallet summary and financial overview |
| `S3` | Transaction History Screen | Shared transaction and money history screen |
| `S4` | Payment Methods Screen | Payment instrument management screen |
| `S5` | Wallet Modal Screen | Quick wallet-access modal |
| `S6` | Support Screen | Shared help and issue-resolution screen |
| `S7` | Profile Screen | Customer profile screen |
| `S8` | Vendor Profile Screen | Vendor profile screen |
| `S9` | Rider Profile Screen | Rider profile screen |
| `S10` | Ratings Screen | Shared trust and reputation screen |
| `S11` | Settings Screen | Customer settings screen |
| `S12` | Settings Screen (Vendor) | Vendor settings screen |
| `S13` | Settings Screen (Rider) | Rider settings screen |
| `S14` | Settings Screen (Global) | Cross-app settings or platform-level settings screen |

### 3.3 Customer IDs

| ID | Name | Definition |
| --- | --- | --- |
| `C1` | Home / Explore Screen | Main customer discovery entry screen |
| `C2` | Search Results Screen | Search and filtering results screen |
| `C3` | Product Detail Screen | Product evaluation screen |
| `C4` | Service Detail Screen | Service evaluation screen |
| `C5` | Events Feed Screen | Event and deal discovery feed |
| `C6` | Event Detail Screen | Event detail and decision screen |
| `C7` | Vendor Map / Nearby Sellers Screen | Seller availability and proximity screen |
| `C8` | Vendor Selection Screen | Seller comparison and fulfillment-choice screen |
| `C9` | Provider List Screen | Service provider comparison screen |
| `C10` | Service Mode Selection Screen | Service-mode choice screen |
| `C11` | Payment Flow Screen | Checkout confirmation and payment screen |
| `C12` | Service Request Screen | Service booking submission screen |
| `C13` | Participation Screen | Event participation and interaction screen |
| `C14` | Event Marketplace Screen | Event-vendor commerce screen |
| `C15` | Order List Screen | Customer order list screen |
| `C16` | Order Detail Screen | Single customer order detail screen |
| `C17` | Order Tracking Screen | Customer order-tracking screen |
| `C18` | Service Status Screen | Service progress screen |
| `C19` | Event Tracking Screen | Event-linked order or participation progress screen |

### 3.4 Vendor IDs

| ID | Name | Definition |
| --- | --- | --- |
| `V1` | Vendor Dashboard Screen | Vendor operations overview |
| `V2` | Analytics Screen | Vendor business-performance screen |
| `V3` | Inventory List Screen | Vendor listing management overview |
| `V4` | Add Product Screen | Product creation screen |
| `V5` | Add Service Screen | Service creation screen |
| `V6` | Edit Item Screen | Listing update screen |
| `V7` | Request Inbox Screen | Incoming requests and demand queue |
| `V8` | Order Detail Screen (Vendor View) | Vendor-side request detail screen |
| `V9` | Fulfillment Center Screen | Order or service execution control screen |
| `V10` | Event List Screen | Event opportunity browse screen |
| `V11` | Event Detail Screen | Vendor-side event detail screen |
| `V12` | Participation Screen | Vendor event-participation screen |
| `V13` | Vendor Profile Screen | Vendor trust and profile screen |
| `V14` | Ratings Screen | Vendor reputation screen |

### 3.5 Rider IDs

| ID | Name | Definition |
| --- | --- | --- |
| `R1` | Rider Home Screen | Rider landing and readiness screen |
| `R2` | Availability Toggle Screen | Rider online or offline control screen |
| `R3` | Job Feed Screen | Available delivery jobs list |
| `R4` | Job Detail Screen | Single job evaluation screen |
| `R5` | Accept / Reject Screen | Job assignment confirmation screen |
| `R6` | Live Navigation Screen | Route-execution screen |
| `R7` | Delivery Tracking Screen | Delivery progress and milestone screen |
| `R8` | Completion Screen | Delivery completion and closure screen |
| `R9` | Earnings Overview Screen | Rider earnings summary screen |
| `R10` | Withdrawals Screen | Rider payout request screen |
| `R11` | Earnings History Screen | Rider historical earnings screen |

## 4. Feature ID Definitions

| ID | Name | Definition |
| --- | --- | --- |
| `F-G1` | Auth Session | Authentication and session lifecycle feature |
| `F-G2` | Role Routing | User-type-based shell routing feature |
| `F-G3` | Global Navigation Context | App-wide routing and deep-link context feature |
| `F-G4` | Global Transaction Orchestration | Cross-role transaction coordination feature |
| `F-C1` | Customer Discovery | Customer demand-entry feature |
| `F-C2` | Product Commerce | Product purchase decision feature |
| `F-C3` | Service Booking | Service request and provider-selection feature |
| `F-C4` | Event Discovery and Participation | Event engagement and event-commerce feature |
| `F-C5` | Checkout and Payment | Transaction-confirmation feature |
| `F-C6` | Customer Orders | Post-purchase order-visibility feature |
| `F-V1` | Vendor Operations | Dashboard and analytics feature |
| `F-V2` | Vendor Inventory | Listing-management feature |
| `F-V3` | Vendor Fulfillment | Demand-execution feature |
| `F-V4` | Vendor Events | Vendor event-growth feature |
| `F-V5` | Vendor Trust | Vendor reputation and identity feature |
| `F-R1` | Rider Availability | Rider readiness feature |
| `F-R2` | Rider Job Intake | Rider assignment-decision feature |
| `F-R3` | Rider Delivery Execution | Rider delivery-execution feature |
| `F-R4` | Rider Earnings | Rider work-to-money feature |
| `F-S1` | Notifications | Shared alerting feature |
| `F-S2` | Wallet and Ledger | Shared financial-visibility feature |
| `F-S3` | Support | Shared recovery and help feature |
| `F-S4` | Identity and Profiles | Shared profile and identity feature |
| `F-S5` | Ratings and Trust Signals | Shared reputation feature |
| `F-S6` | Settings and Preferences | Shared preferences feature |

## 5. Naming Rules

| Rule | Meaning |
| --- | --- |
| Use title case in docs | Example: `Product Detail Screen` |
| Use kebab-case for route folders | Example: `product-detail` |
| Use lowercase feature folders | Example: `customer/discovery`, `vendor/fulfillment` |
| Use singular capability names where possible | Example: `checkout`, `inventory`, `support` |
| Keep screen names user-facing | Docs should name what users see, not implementation details |
| Keep feature names business-facing | Features should describe capabilities, not UI widgets |

## 6. Route Naming Guidance

| Concern | Recommended Pattern | Example |
| --- | --- | --- |
| Route groups | Parenthesized role or app area | `(auth)`, `(customer)`, `(vendor)`, `(rider)` |
| Screen route folder or file | Kebab-case business name | `product-detail.tsx`, `order-tracking.tsx` |
| Modal routes | Put under modal group or clear modal name | `wallet-modal.tsx` |
| Shared route labels | Name by user task, not implementation | `support`, not `ticket-center` unless that is the product term |

## 7. Feature Folder Naming Guidance

| Concern | Recommended Pattern | Example |
| --- | --- | --- |
| Role root | `src/features/<role>` | `src/features/customer` |
| Capability folder | `src/features/<role>/<capability>` | `src/features/vendor/inventory` |
| Shared capability | `src/shared/<capability>` | `src/shared/wallet` |
| Internal subfolders | `components`, `screens`, `hooks`, `api`, `types`, `utils` only inside a feature | `src/features/customer/checkout/screens` |

## 8. How To Use This Key

| If You Are Working On | Use |
| --- | --- |
| UX flows | Screen IDs like `C11`, `V9`, `S2` |
| Screen inventory | Screen IDs and user-facing screen names |
| Architecture planning | Feature IDs like `F-C5`, `F-V3` |
| Route creation | Route names derived from screen names |
| Folder creation | Feature folder names from feature definitions |

## 9. Final Rule

If a name appears in a doc, route, or folder, it should be traceable back to one of these:

| Source of Truth | Purpose |
| --- | --- |
| Screen ID | UX and screen planning reference |
| Feature ID | Architecture and ownership reference |
| Feature folder name | Implementation ownership reference |
