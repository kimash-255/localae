# App Full UX Flow

This document combines the product idea, navigation, screen inventory, money flow, and build order into one master UX flow for the whole app.

## 1. Core UX Principle

The app is a local commerce system that should feel simple to the user even though it coordinates multiple actors behind the scenes.

The full product has 4 main UX layers:

| Layer | Purpose | Main Users |
| --- | --- | --- |
| Entry Layer | Boot, auth, role routing | All users |
| Demand Layer | Discovery, search, product/service/event interest | Customers |
| Execution Layer | Vendor fulfillment and rider delivery | Vendors, riders |
| Trust and Settlement Layer | Orders, wallet, notifications, profile, settings | All users |

## 2. Full App Flow At A Glance

| Step | Flow Stage | Primary Screen / Module | Outcome |
| --- | --- | --- | --- |
| 1 | App entry | Splash Screen | Check app state, session, and role |
| 2 | Authentication | Login / Register | User enters system |
| 3 | Role routing | Role Selection / Role Router | User is sent to customer, vendor, or rider app |
| 4 | Customer demand creation | Home, Search, Product, Service, Events | User expresses intent to buy, book, or join |
| 5 | Supply matching | Vendor Map, Vendor Selection, Provider selection | User is matched to available supply |
| 6 | Transaction initiation | Payment Flow / Service Request / Participation | Platform creates transaction record |
| 7 | Vendor execution | Request Inbox, Order Detail, Fulfillment Center | Vendor accepts and prepares work |
| 8 | Rider execution | Job Feed, Job Detail, Navigation, Completion | Rider handles delivery when needed |
| 9 | Customer visibility | Order List, Order Detail, Order Tracking | Customer sees status and progress |
| 10 | Settlement and trust | Wallet, Notifications, Profile, Ratings, Settings | App closes the loop and supports repeat use |

## 3. Entry UX Flow

| Order | Screen | User Type | Purpose | Next |
| --- | --- | --- | --- | --- |
| 1 | Splash Screen | All | Load app, validate token, fetch role | Login or Role Router |
| 2 | Login Screen | All | Sign in existing user | Role Router |
| 3 | Register Screen | All | Create new account | Role Selection or Role Router |
| 4 | Role Selection Screen | All | Assign role if not yet defined | Customer, Vendor, or Rider app |

## 4. Customer UX Flow

### 4.1 Customer Master Journey

| Stage | Screen / Module | User Goal | System Goal |
| --- | --- | --- | --- |
| Discover | Home / Explore | Find products, services, or events nearby | Surface relevant local demand paths |
| Narrow | Search Results | Filter what is available | Reduce search friction |
| Evaluate | Product Detail / Service Detail / Event Detail | Understand the offer | Build trust and conversion |
| Match | Vendor Map / Nearby Sellers / Provider choice | Find who can fulfill | Route demand to supply |
| Decide | Vendor Selection / Service Mode / Participation | Choose fulfillment path | Standardize transaction logic |
| Pay or Request | Payment Flow / Service Request | Confirm order or booking | Create transaction record |
| Monitor | Order List / Order Detail / Order Tracking | Follow progress | Reduce uncertainty |
| Settle and Return | Wallet, Notifications, Profile | Review payments and activity | Increase retention and repeat use |

### 4.2 Customer Product Commerce Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Home / Explore | Entry discovery hub | User finds an item |
| 2 | Search Results | Search and filtering | Shortlist of relevant items |
| 3 | Product Detail | Product evaluation | Purchase intent |
| 4 | Vendor Map / Nearby Sellers | View local availability | Nearby supply options |
| 5 | Vendor Selection | Choose seller and fulfillment method | Selected vendor |
| 6 | Payment Flow | Confirm transaction | Order created |
| 7 | Order Tracking | Follow fulfillment | Order completion |

### 4.3 Customer Service Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Home / Explore | Discover service categories | Interest in a service |
| 2 | Search Results | Find relevant providers or services | Shortlist |
| 3 | Service Detail | Evaluate service | Booking intent |
| 4 | Provider List | Compare providers | Selected provider |
| 5 | Service Mode Selection | Choose onsite, remote, or scheduled mode | Service mode locked |
| 6 | Service Request | Submit booking | Service request created |
| 7 | Service Status | Track progress | Service completion |

### 4.4 Customer Events Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Home / Explore / Events entry | Discover current events or deals | Event interest |
| 2 | Events Feed | Browse live opportunities | Shortlist |
| 3 | Event Detail | Review event info and offers | Intent to join or buy |
| 4 | Participation Screen | Join, interact, or purchase | Participation created |
| 5 | Event Marketplace | Buy from event vendors | Event order created |
| 6 | Event Tracking | Track attendance or event-linked orders | Event outcome |

## 5. Vendor UX Flow

### 5.1 Vendor Master Journey

| Stage | Screen / Module | Vendor Goal | System Goal |
| --- | --- | --- | --- |
| Operate | Vendor Dashboard | See business status | Give operational overview |
| Configure | Inventory List, Add Product, Add Service, Edit Item | Manage supply | Keep listings structured and current |
| Respond | Request Inbox, Order Detail | Review incoming demand | Turn demand into accepted work |
| Fulfill | Fulfillment Center | Process orders or services | Move transactions toward completion |
| Grow | Event List, Event Detail, Participation | Join event-based demand opportunities | Increase volume |
| Trust and visibility | Vendor Profile, Ratings | Build reputation | Improve confidence and conversion |

### 5.2 Vendor Order Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Vendor Dashboard | View activity and incoming demand | Operational awareness |
| 2 | Request Inbox | Accept or reject new requests | Accepted work |
| 3 | Order Detail Screen (Vendor View) | Inspect request details | Fulfillment decision |
| 4 | Fulfillment Center | Prepare, confirm, hand off, or complete | Work executed |
| 5 | Notifications / Wallet / Analytics | Review outcomes and earnings | Business feedback loop |

### 5.3 Vendor Inventory Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Inventory List Screen | View current listings | Listing overview |
| 2 | Add Product Screen | Add a sellable product | New product |
| 3 | Add Service Screen | Add a service offering | New service |
| 4 | Edit Item Screen | Update an existing listing | Improved listing quality |

### 5.4 Vendor Events Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Event List Screen | Browse available events | Candidate events |
| 2 | Event Detail Screen | Review event opportunity | Decision to join |
| 3 | Participation Screen | Join and manage presence | Event participation active |

## 6. Rider UX Flow

### 6.1 Rider Master Journey

| Stage | Screen / Module | Rider Goal | System Goal |
| --- | --- | --- | --- |
| Become available | Rider Home, Availability Toggle | Signal readiness for jobs | Activate logistics capacity |
| Receive work | Job Feed, Job Detail | Review available jobs | Match supply to delivery demand |
| Commit | Accept / Reject | Take a job | Lock rider assignment |
| Deliver | Live Navigation, Delivery Tracking | Execute the route | Move transaction physically |
| Close | Completion | Finish job | Confirm delivery outcome |
| Get paid | Earnings Overview, Withdrawals, Earnings History | Track income | Close rider settlement loop |

### 6.2 Rider Delivery Flow

| Order | Screen | Purpose | Output |
| --- | --- | --- | --- |
| 1 | Rider Home Screen | Landing state and readiness | Rider context |
| 2 | Availability Toggle Screen | Go online for jobs | Active rider status |
| 3 | Job Feed Screen | See available deliveries | Candidate jobs |
| 4 | Job Detail Screen | Inspect a delivery request | Accept decision |
| 5 | Accept / Reject Screen | Confirm assignment | Rider assigned |
| 6 | Live Navigation Screen | Execute route in real time | Delivery in motion |
| 7 | Delivery Tracking Screen | Track active progress | Status visibility |
| 8 | Completion Screen | Finish the delivery | Job completed |
| 9 | Earnings Overview / Withdrawals / History | Review money earned | Settlement visibility |

## 7. Shared System UX Flow

| Module | Who Uses It | Purpose | When It Appears |
| --- | --- | --- | --- |
| Notifications | All users | Alerts, status changes, updates | Before, during, and after transactions |
| Wallet | Customer, vendor, rider | Payment history, earnings, withdrawals, settlements | After transactions begin |
| Support | All users | Resolve issues and friction | At any failure or help point |
| Profile | Customer, vendor, rider | Identity, trust, activity summary | After onboarding |
| Ratings | Vendors, riders, possibly customers | Trust and reputation | After fulfilled transactions |
| Settings | All users | Preferences and account controls | Throughout lifecycle |

## 8. Money UX Flow

| Stage | What User Experiences | What System Does |
| --- | --- | --- |
| Initiation | Customer confirms order, booking, or participation | Create transaction record |
| Execution | Vendor or rider performs real-world work | Track fulfillment state |
| Splitting | Usually invisible to end user | Split value between vendor, rider, and platform |
| Settlement | User sees payment status, earnings, or debt position | Reconcile ledgers and balances |

## 9. Full Cross-Role End-To-End Flow

| Step | Customer | Vendor | Rider | Platform |
| --- | --- | --- | --- | --- |
| 1 | Opens app | - | - | Boot and authenticate |
| 2 | Discovers item or service | - | - | Surface local options |
| 3 | Chooses vendor or provider | Receives potential demand | - | Match demand to supply |
| 4 | Confirms payment or request | Receives request | - | Create transaction |
| 5 | Watches order status | Accepts and prepares | Receives job if delivery is needed | Coordinate execution |
| 6 | Tracks progress | Hands off or completes service | Delivers order | Update states |
| 7 | Receives completion | Gets paid / credited | Gets paid / credited | Split and settle value |
| 8 | Can reorder or continue browsing | Reviews performance | Reviews earnings | Reinforce retention loop |

## 10. Recommended UX Implementation Phases

| Phase | Scope | What It Proves |
| --- | --- | --- |
| Phase 1 | Splash, Auth, Customer Home, Search, Product Detail, Vendor Selection, Payment, Order Tracking | Core customer commerce loop |
| Phase 2 | Vendor Dashboard, Request Inbox, Order Detail, Fulfillment Center | Vendor-side execution |
| Phase 3 | Rider Home, Job Feed, Navigation, Completion, Earnings | Delivery and last-mile execution |
| Phase 4 | Wallet, Notifications, Support, Ratings, settings refinement | Trust, settlement, and polish |

## 11. Architecture Implication

This UX flow supports a role-based feature architecture:

| Area | Best Ownership |
| --- | --- |
| Auth and entry flow | `features/auth` |
| Customer journey | `features/customer/*` |
| Vendor journey | `features/vendor/*` |
| Rider journey | `features/rider/*` |
| Cross-cutting reusable pieces | `shared/*` |

## 12. Final Rule

The app should always feel like one smooth system even though it contains 3 role-based apps inside it.

That means:

| Rule | Meaning |
| --- | --- |
| Discovery should lead directly to action | Users should not get lost between browsing and buying |
| Role areas should stay clean | Customer, vendor, and rider flows should not bleed into each other unnecessarily |
| Shared modules should support all roles | Wallet, notifications, support, settings, and reusable UI should stay cross-cutting |
| Transaction visibility should be continuous | Every actor should understand what is happening next |
