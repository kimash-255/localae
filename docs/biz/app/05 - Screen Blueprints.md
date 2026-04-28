
---
We follow your structure:

## 1. AuthStack

## 2. CustomerApp

## 3. VendorApp

## 4. RiderApp

## 5. GlobalModalStack

---

# 🔐 1 — AUTH STACK SCREEN BLUEPRINTS

# 📱 1. SplashScreen

## 🎯 Purpose

Initial system boot + auth state check

---

## 🧭 Entry

App launch

## Exit

* AuthStack (not logged in)
* RoleRouter (logged in)

---

## 🧩 UI STRUCTURE

```text
[Logo / Brand Animation]
[Loading Indicator]
[Optional: Tagline]
```

---

## 🧠 INTERACTIONS

* None (non-interactive)
* Auto navigation after auth check

---

## 🔁 SYSTEM ACTIONS

* Check token
* Validate session
* Fetch user role

---

---

# 🔐 2. LoginScreen

## 🎯 Purpose

Authenticate user into system

---

## 🧭 Entry

* SplashScreen
* Logged out session

## Exit

* RoleRouter (after login)

---

## 🧩 UI STRUCTURE

```text
[App Logo]

[Phone Number Input]
[Password Input]

[Login Button]

[Divider: OR]

[Login with OTP]

[Forgot Password Link]
```

---

## 🧠 INTERACTIONS

* Login with credentials
* Login with OTP
* Navigate to RegisterScreen

---

## 🔁 SYSTEM ACTIONS

* Authenticate user
* Fetch role (customer/vendor/rider)
* Store token
* Redirect to RoleRouter

---

---

# 🧾 3. RegisterScreen

## 🎯 Purpose

Create new user account

---

## 🧭 Entry

LoginScreen

## Exit

RoleRouter

---

## 🧩 UI STRUCTURE

```text
[Name Input]
[Phone Number]
[Password]
[Confirm Password]

[Continue Button]
```

---

## 🧠 INTERACTIONS

* Submit registration
* Validate input

---

## 🔁 SYSTEM ACTIONS

* Create user account
* Assign default role (or ask next step)
* Store session

---

---

# 🧭 4. RoleRouterScreen

## 🎯 Purpose

Assign user role if not predefined

---

## 🧭 Entry

After registration OR override

## Exit

RoleRouter → correct app

---

## 🧩 UI STRUCTURE

```text
[Choose Your Role]

[Customer Card]
- Shop / Buy / Order

[Vendor Card]
- Sell / Manage Inventory

[Rider Card]
- Deliver / Earn
```

---

## 🧠 INTERACTIONS

* Select role
* Confirm selection

---

## 🔁 SYSTEM ACTIONS

* Save role to user profile
* Update backend user type
* Redirect to RoleRouter

---

---

# 🧠 AUTH STACK FLOW (COMPLETE)

```text
SplashScreen
   ↓
Login / Register
   ↓
Role is already created during registration
   ↓
RoleRouter → App Shell
```

---



# 2🏠 CUSTOMER APP — 1. HOMESCREEN (EXPLORE ENGINE)

This is your **most important screen in the entire system** because it controls:

* discovery (A: products)
* services (B)
* events (C)
* and funnels everything into vendor selection

---

# 🎯 PURPOSE

> Help users instantly find *what they want* and route them to the nearest available supply (product / service / event).

This is not a “homepage”.

It is:

> 🧠 **Demand-to-supply routing engine**

---

# 🧭 ENTRY POINTS

* After login (default landing)
* Bottom tab: Home
* Returning user session
* Deep links (product/service/event)

---

# 🧩 UI STRUCTURE (DESIGN BLUEPRINT)

```text id="home_ui_1"
[Top Bar]
- Location selector (auto-detect + manual change)
- Search bar (primary action)

[Quick Categories Row]
- Food
- Electronics
- Fashion
- Services
- Events

[Main Feed Section]
→ Mixed intelligent feed:
   - Nearby Products
   - Nearby Services
   - Trending Events

[“Near You” Section]
- Horizontal product cards
- Distance + price range + availability

[Service Shortcuts Section]
- Barber
- Laundry
- Repair
- Cleaning

[Event Spotlight Section]
- Upcoming nearby events
- “Join” CTA

[Bottom Navigation Tabs]
Home | Search | Orders | Wallet | Profile
```

---

# 🧠 INFORMATION ARCHITECTURE

This screen is NOT static.

It is built from 4 dynamic engines:

---

## 🟣 1. PRODUCT ENGINE (A)

Shows:

* items nearby
* price variations
* availability signals

---

## 🟣 2. SERVICE ENGINE (B)

Shows:

* service categories
* availability
* “can come to you / go there / pickup”

---

## 🟣 3. EVENT ENGINE (C)

Shows:

* active events nearby
* vendor clusters
* deals + promotions

---

## 🟣 4. INTENT ENGINE (SEARCH SIGNALS)

If user behavior is known:

* repeat food searches → food feed bias
* frequent repairs → service bias

---

# 🧠 INTERACTIONS

---

## 🔍 SEARCH BAR (PRIMARY ACTION)

* tap → SearchStack
* autocomplete suggestions:

  * products
  * services
  * events

---

## 🟢 CATEGORY TAP

* filters entire feed instantly
* routes into SearchResultsScreen logic

---

## 📦 PRODUCT CARD TAP

→ opens:

👉 ProductDetailScreen

---

## 🧑‍🔧 SERVICE TAP

→ opens:

👉 ServiceDetailScreen

---

## 🎪 EVENT TAP

→ opens:

👉 EventDetailScreen

---

## 📍 LOCATION CHANGE

* refreshes:

  * nearby vendors
  * availability
  * pricing

---

# 🔁 SYSTEM ACTIONS

When screen loads:

```text id="home_sys_1"
1. Detect user location
2. Fetch:
   - nearby products (A)
   - nearby services (B)
   - nearby events (C)
3. Rank results by:
   - distance
   - availability
   - trust score
   - popularity
```

---

When user interacts:

* logs intent signals
* improves feed ranking model
* updates recommendation engine

---

# 🧠 UX PRINCIPLES

## 1. SPEED FIRST

User should find something in <3 seconds

## 2. NO DEAD ENDS

Every scroll leads to:

* product
* service
* event

## 3. LOCATION IS CORE

Everything is geo-aware

## 4. NO CART THINKING

Everything is:

> “What is available near me right now?”

---

# 🔥 CORE ROLE OF HOMESCREEN 

This screen is:

> 🧠 THE ENTRY POINT OF ALL MONEY FLOW

Because it routes into:

* Product → VendorSelection → TRX
* Service → Provider selection → TRX
* Event → Marketplace inside event → TRX

> 🔁 REAL-TIME SUPPLY MAP

---

# 🧭 HOMESCREEN FLOW

```text id="home_flow_1"
Open App
   ↓
HomeScreen loads
   ↓
Detect location
   ↓
Fetch A + B + C
   ↓
User taps item
   ↓
Product / Service / Event detail
   ↓
Vendor selection OR action
```

---
---

# 📱 CUSTOMER APP — 2. PRODUCT DETAIL SCREEN

# 🎯 PURPOSE

> Show a product as a **shared demand object**, then route the user to the best fulfillment option (vendor / delivery / shop visit).

This screen does NOT sell directly.

It:

* aggregates supply
* compares vendors
* triggers order creation flow

---

# 🧭 ENTRY POINTS

* HomeScreen (product tap)
* SearchResultsScreen
* Event marketplace
* Deep links

---

# 🧩 UI STRUCTURE (DESIGN BLUEPRINT)

```text id="pd_ui_1"
[Product Image Gallery]

[Product Name]
[Category Tag]

[Quick Summary]
- “Available near you”

[Price Range Block]
- Lowest price → Highest price
- “Varies by vendor”

────────────────────

[NEARBY VENDORS SECTION]

Vendor Card (repeated list):
- Vendor name
- Distance
- Price
- Stock status (In stock / Limited / Unknown)
- Trust rating
- Fulfillment options:
   • Pickup
   • Delivery
   • Walk-in

[Primary CTA per vendor]
→ “Select Vendor”

────────────────────

[GLOBAL ACTION SECTION]

[Button 1]
→ View All Vendors

[Button 2]
→ Request This Item

[Button 3]
→ Go to Nearest Shop

────────────────────

[INFO SECTION]
- Product description
- Variants (if any)
- Category info
```

---

# 🧠 CORE CONCEPT (VERY IMPORTANT)

A product is NOT tied to a vendor.

Instead:

> 🧩 Product = demand layer
> 🏪 Vendors = supply layer

This screen bridges them.

---

# 🔁 USER INTERACTIONS

---

## 🟢 1. TAP VENDOR CARD

→ Opens:

👉 VendorSelectionScreen

---

## 🟡 2. “REQUEST THIS ITEM”

Triggers:

```text id="pd_flow_1"
GlobalModalStack → PaymentFlowScreen
```

BUT:

* no payment yet finalized
* creates pending TRX intent

---

## 🔵 3. “GO TO NEAREST SHOP”

* selects closest vendor automatically
* opens navigation or vendor map

---

## 🟣 4. “VIEW ALL VENDORS”

→ full comparison list (VendorSelectionScreen)

---

# 🧠 SYSTEM ACTIONS

When screen loads:

```text id="pd_sys_1"
1. Fetch product metadata
2. Query all vendors with item
3. Rank vendors by:
   - distance
   - price
   - availability
   - trust score
4. Build dynamic vendor list
```

---

When user interacts:

* logs intent signal:

  * price-sensitive
  * proximity-sensitive
  * urgency
* feeds recommendation engine

---

# 🔥 THIS SCREEN IS YOUR CORE DIFFERENTIATOR

Because it enables:

## 🧠 Traditional apps:

* product → single seller → checkout

## 🚀 Your system:

* product → multiple vendors → intelligent routing

---

# 🧭 UX PRINCIPLES

## 1. COMPARISON FIRST

User must see multiple options immediately

## 2. NO SINGLE SELLER LOCK-IN

Every product is multi-vendor by default

## 3. TRUST IS VISUAL

Distance + rating + availability matter more than branding

## 4. ACTION ALWAYS CLEAR

User always knows:

* buy
* request
* go there

> 🧠 **Dynamic marketplace routing layer**

---

# 🧭 PRODUCT DETAIL FLOW

```text id="pd_flow_2"
Home/Search
   ↓
ProductDetailScreen
   ↓
Vendor comparison
   ↓
Select vendor OR request
   ↓
PaymentFlow (TRX creation)
   ↓
Order lifecycle starts
```

---
# 🏪 CUSTOMER APP — 3. VENDOR SELECTION SCREEN
> 🧠 **Commitment to a specific supply source**

---

# 🎯 PURPOSE

> Let the user compare vendors for the same product and choose **who fulfills the demand** and **how (pickup / delivery / walk-in).**

This is the **conversion screen**.

---

# 🧭 ENTRY POINTS

* ProductDetailScreen (“View all vendors”)
* HomeScreen quick vendor taps
* Search results product tap
* Event marketplace product/service tap

---

# 🧩 UI STRUCTURE (DESIGN BLUEPRINT)

```text id="vs_ui_1"
[Product Summary Bar]
- Product name
- Image thumbnail
- Quick price range

────────────────────

[FILTER BAR]
- Distance
- Price
- Rating
- Availability
- Fulfillment type:
   • Pickup
   • Delivery
   • Walk-in

────────────────────

[VENDOR LIST (CORE SECTION)]

Each Vendor Card:

┌────────────────────────────┐
│ Vendor Name + Trust Score  │
│ Distance (e.g. 1.2 km)     │
│ Price: 450–500 KES         │
│ Stock: In stock / Low      │
│                            │
│ Fulfillment Options:       │
│ ✔ Walk-in                  │
│ ✔ Delivery                 │
│ ✔ Pickup                  │
│                            │
│ [Select Vendor Button]    │
└────────────────────────────┘

────────────────────

[MAP PREVIEW (OPTIONAL)]
- pins of vendors nearby

────────────────────

[PRIMARY ACTION BAR]
→ “Continue with Selected Vendor”
```

---

# 🧠 CORE CONCEPT

This screen is NOT just selection.

It is:

> 🧩 **Supply-side negotiation layer**

User is choosing:

* price
* distance
* trust
* speed
* fulfillment method

---

# 🔁 USER INTERACTIONS

---

## 🟢 1. SELECT VENDOR CARD

* highlights vendor
* updates summary bar

---

## 🟡 2. CHANGE FILTERS

* instantly reorders vendors:

  * cheapest
  * closest
  * fastest delivery
  * best rated

---

## 🔵 3. VIEW ON MAP

* switches to spatial view
* shows vendor distribution

---

## 🟣 4. CONTINUE BUTTON

→ triggers:

```text id="vs_flow_1"
GlobalModalStack → PaymentFlowScreen
```

OR

→ OrderCreation engine starts TRX draft

---

# 🧠 SYSTEM ACTIONS

When screen loads:

```text id="vs_sys_1"
1. Receive product ID
2. Fetch all vendors with:
   - stock status
   - pricing
   - location
3. Compute ranking score:
   score = (distance + price + trust + speed)
4. Render sorted vendor list
```

---

When user selects vendor:

* locks vendor for TRX draft
* reserves intent state (not payment yet)
* prepares fulfillment logic

---

# 🔥 CRITICAL ROLE IN YOUR SYSTEM

This screen is where:

## BEFORE:

* product is just intent

## AFTER:

* product becomes **assigned supply contract**

---

# 🧭 UX PRINCIPLES

## 1. TRANSPARENCY FIRST

User must see:

* why a vendor is ranked higher

## 2. NO HIDDEN DECISIONS

No automatic vendor assignment

## 3. FAST DECISION PATH

User should select vendor in <10 seconds

## 4. TRUST SIGNALS DOMINATE

Distance + reliability > branding

---

# ⚠️ WHAT THIS SCREEN REPLACES

You eliminate:

* “Add to cart”
* single checkout vendor lock-in
* static product pricing pages

Instead you introduce:

> 🧠 **Multi-vendor real-time marketplace selection**

---

# 🧭 VENDOR SELECTION FLOW

```text id="vs_flow_2"
ProductDetailScreen
   ↓
VendorSelectionScreen
   ↓
User selects vendor
   ↓
TRX draft created
   ↓
PaymentFlowScreen (finalization)
   ↓
Order lifecycle begins
```

---
# 💳 GLOBAL MODAL STACK — PAYMENT FLOW SCREEN (TRX ENGINE CORE)

> 🧠 **Transaction creation, confirmation, and settlement engine (TRX System)**

---

# 🎯 PURPOSE

> Convert user intent (selected vendor/service/event) into a **formal transaction (TRX)** and define how money moves across all actors.

This is where:

* order becomes real
* vendor is committed
* rider (if needed) is assigned
* platform revenue is locked in

---

# 🧭 ENTRY POINTS

Triggered from:

* ProductDetailScreen → Request action
* VendorSelectionScreen → Continue
* Service request (B flow)
* Event purchase / participation
* Rider assignment trigger (if delivery needed)

---

# 🧩 UI STRUCTURE (DESIGN BLUEPRINT)

```text id="pf_ui_1"
[Transaction Summary Card]
- Product / Service name
- Selected Vendor / Provider
- Price breakdown (estimated)

────────────────────

[FULFILLMENT MODE]

- 🏪 Walk-in (no rider)
- 🛵 Delivery (rider required)
- 🧑‍🔧 Service visit (provider moves)
- 📦 Item pickup (rider moves item)

────────────────────

[COST BREAKDOWN]

- Item/Service Price
- Delivery Fee (if applicable)
- Platform Fee
- Total Amount

────────────────────

[PAYMENT METHOD]

- M-Pesa
- Cash (recorded)
- Wallet balance

────────────────────

[CONFIRMATION SECTION]

[Confirm Button]
→ “Create Transaction”

────────────────────

[STATUS NOTE]
- “This will notify vendor immediately”
- “Rider assigned if needed”
```

---

# 🧠 CORE CONCEPT

This screen does NOT just “pay”.

It creates:

> 🧾 **TRX = Transaction Object (system record of economic action)**

---

# 🔁 USER INTERACTIONS

---

## 🟢 1. CONFIRM TRANSACTION

Triggers:

```text id="pf_flow_1"
Create TRX object:
- customer ID
- vendor/provider ID
- rider (optional)
- item/service/event
- fulfillment mode
- total amount
- platform fee
```

---

## 🟡 2. SELECT PAYMENT METHOD

### M-Pesa:

* instant settlement
* auto split logic

### Cash:

* creates “pending settlement debt ledger”

---

## 🔵 3. CHANGE FULFILLMENT MODE

User can switch:

* Walk-in → no rider
* Delivery → rider assigned
* Provider visit → scheduling logic

---

# 🧠 SYSTEM ACTIONS (VERY IMPORTANT)

When screen loads:

```text id="pf_sys_1"
1. Receive selected vendor + item/service
2. Calculate pricing breakdown:
   - base price
   - delivery estimate (if needed)
   - platform fee
3. Check availability:
   - vendor stock confirmation
4. Prepare TRX draft (NOT final yet)
```

---

When user confirms:

```text id="pf_sys_2"
1. Create TRX record
2. Lock vendor inventory (if product)
3. Notify vendor instantly
4. Assign rider (if delivery mode)
5. Update order lifecycle state:
   → PENDING_CONFIRMATION / PREPARING
```

---
it connects:

## 🧍 CUSTOMER

→ intent

## 🏪 VENDOR

→ supply execution

## 🛵 RIDER

→ logistics execution

## 🌐 PLATFORM

→ revenue capture

---

# 🧭 UX PRINCIPLES

## 1. TRANSPARENCY OF MONEY

User must always see:

* what they are paying
* why they are paying it

---

## 2. ZERO SURPRISES

No hidden fees, no late changes

---

## 3. SPEED TO CONFIRMATION

This screen should be completed in <5 seconds

---

## 4. FULFILLMENT IS PART OF PAYMENT

Payment ≠ just money → it defines movement model

---

> 🧠 **Real-time transaction orchestration system**

---

# 🧭 PAYMENT FLOW SYSTEM MAP

```text id="pf_flow_2"
Product / Service / Event
   ↓
Vendor Selection
   ↓
PaymentFlowScreen
   ↓
TRX CREATED
   ↓
System actions:
   - vendor notified
   - rider assigned (if needed)
   - order state initialized
   ↓
Order lifecycle begins
```

---
# 📦 CUSTOMER APP — 4 ORDERS STACK (LIFECYCLE SYSTEM)

After PaymentFlowScreen creates a TRX, everything moves here.

> 🧠 This is where users track “what is happening in the real world”

---

# 🎯 PURPOSE

> Give the customer full visibility and control over all active, completed, and past transactions.

This screen family answers:

* Did the vendor accept?
* Is it being prepared?
* Where is the rider?
* Is it completed?

---

# 🧭 STACK STRUCTURE

```text id="orders_stack_1"
OrdersStack
├── OrderListScreen
├── OrderDetailScreen
├── OrderTrackingScreen
```

---

# 📱 1. ORDER LIST SCREEN

## 🎯 PURPOSE

Show all user transactions (active + history)

---

## 🧩 UI STRUCTURE

```text id="ol_ui_1"
[Tabs Filter]
- Active
- Completed
- Cancelled

────────────────────

[ORDER CARD LIST]

Each Order Card:

┌────────────────────────────┐
│ Product / Service Name     │
│ Vendor Name                │
│ Status: Preparing / On way │
│ Price                     │
│ Timestamp                │
│                            │
│ [Track Order Button]      │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap order card → OrderDetailScreen
* Tap “Track Order” → OrderTrackingScreen
* Filter tabs → switch datasets

---

## 🔁 SYSTEM ACTIONS

* Fetch all TRX records for user
* Categorize by status:

  * PENDING
  * CONFIRMED
  * IN_PROGRESS
  * COMPLETED
  * CANCELLED

---

# 📱 2. ORDER DETAIL SCREEN

## 🎯 PURPOSE

Show full transaction breakdown and status history

---

## 🧩 UI STRUCTURE

```text id="od_ui_1"
[Order Header]
- Product / Service
- Vendor name
- Order ID

────────────────────

[STATUS TIMELINE]

- Request Sent
- Vendor Confirmed
- Payment Confirmed
- Rider Assigned (if any)
- In Progress
- Completed

────────────────────

[FULFILLMENT INFO]
- Mode: Delivery / Walk-in / Provider Visit
- Rider info (if applicable)
- Location details

────────────────────

[PAYMENT BREAKDOWN]
- Item cost
- Delivery fee
- Platform fee
- Total paid

────────────────────

[ACTIONS]
- Contact Vendor
- Contact Rider
- Cancel Order (if allowed)
```

---

## 🧠 INTERACTIONS

* Expand status steps
* Open maps for rider tracking
* Contact actors (vendor/rider)

---

## 🔁 SYSTEM ACTIONS

* Fetch TRX full details
* Fetch rider assignment (if exists)
* Fetch vendor status updates

---

# 📱 3. ORDER TRACKING SCREEN (REAL-TIME LAYER)

## 🎯 PURPOSE

Show live movement of order in real world

---

## 🧩 UI STRUCTURE

```text id="ot_ui_1"
[Live Map View]

- Vendor location pin
- Rider location (if active)
- Customer location

────────────────────

[LIVE STATUS PANEL]

Status:
- Preparing
- Picked up
- In transit
- Arriving soon

────────────────────

[RIDER CARD (IF ACTIVE)]
- Name
- Vehicle type
- Call / chat button

────────────────────

[ETA DISPLAY]
- Estimated time remaining
```

---

## 🧠 INTERACTIONS

* Zoom map
* Track rider movement
* Contact rider/vendor
* Refresh live status

---

## 🔁 SYSTEM ACTIONS

* Subscribe to real-time updates:

  * rider GPS stream
  * vendor status updates
  * TRX state changes

---

# 🔥 CORE CONCEPT OF ORDERS STACK

> 🧠 **Real-world state mirror of your TRX system**

---

# 🧭 ORDER LIFECYCLE FLOW

```text id="orders_flow_1"
PaymentFlowScreen
   ↓
TRX CREATED
   ↓
OrderListScreen (appears as ACTIVE)
   ↓
OrderDetailScreen (full context)
   ↓
OrderTrackingScreen (live execution)
   ↓
COMPLETED STATE
```

---

# 🧠 STATE MODEL 

Each order moves through:

```text id="orders_state_1"
PENDING_CONFIRMATION
→ CONFIRMED
→ PREPARING
→ ASSIGNED_TO_RIDER
→ IN_TRANSIT
→ COMPLETED
→ ARCHIVED
```

---

# 💡 UX PRINCIPLES

## 1. ALWAYS TRANSPARENT

User always knows:

* where money is
* who has responsibility
* what is happening next

---

## 2. REAL-TIME FEEL

Orders must feel “alive”, not static receipts

---

## 3. SINGLE SOURCE OF TRUTH

OrdersStack = only truth of transaction state

---

## 4. NO CONFUSION BETWEEN ACTORS

Clearly separate:

* Vendor actions
* Rider actions
* System actions

---

# 💳 CUSTOMER APP — WALLET STACK (FINANCIAL CONTROL LAYER)

> 🧠 **Personal financial ledger inside your ecosystem**

---

# 🎯 PURPOSE

> Let users see, manage, and control all money movement in and out of the platform.

This includes:

* payments
* refunds
* wallet balance
* transaction breakdowns
* saved payment methods

---

# 🧭 STACK STRUCTURE

```text id="wallet_stack_1"
WalletStack
├── WalletHomeScreen
├── TransactionHistoryScreen
├── PaymentMethodsScreen
```

---

# 📱 1. WALLET HOME SCREEN

## 🎯 PURPOSE

Show user’s financial snapshot in real time

---

## 🧩 UI STRUCTURE

```text id="wh_ui_1"
[Balance Card]
- Available Balance
- Pending Balance (from active orders)
- Lifetime Spend

────────────────────

[Quick Actions]
- Add Money
- Withdraw (if enabled)
- View Transactions

────────────────────

[Recent Activity Preview]
- Last 5 transactions

────────────────────

[Insight Card]
- “You spent X on food this week”
- “Most used vendor: XYZ”
```

---

## 🧠 INTERACTIONS

* Tap balance → full breakdown
* Tap transaction → TransactionHistoryScreen
* Tap add money → payment flow modal

---

## 🔁 SYSTEM ACTIONS

* Aggregate all TRX records
* Compute balances:

  * completed payments
  * pending holds
  * refunds

---

# 📱 2. TRANSACTION HISTORY SCREEN

## 🎯 PURPOSE

Show full financial ledger (all money movement)

---

## 🧩 UI STRUCTURE

```text id="th_ui_1"
[Filter Tabs]
- All
- Payments
- Refunds
- Earnings adjustments

────────────────────

[TRANSACTION LIST]

Each Item:

┌────────────────────────────┐
│ Vendor / Service / Event   │
│ Type: Payment / Refund     │
│ Amount                     │
│ Status: Completed / Pending│
│ Date                       │
│                            │
│ [View Details]            │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap transaction → expanded detail view
* Filter by type
* Search transaction history

---

## 🔁 SYSTEM ACTIONS

* Fetch full TRX ledger
* Classify transactions:

  * inflow
  * outflow
  * adjustments

---

# 📱 3. PAYMENT METHODS SCREEN

## 🎯 PURPOSE

Manage how user pays inside system

---

## 🧩 UI STRUCTURE

```text id="pm_ui_1"
[Saved Methods]

- M-Pesa (primary)
- Cash preference toggle
- Future: Card / Wallet

────────────────────

[Add New Method]
- Add M-Pesa number
- Verify account

────────────────────

[Default Method Selector]
- Set preferred payment method
```

---

## 🧠 INTERACTIONS

* Add payment method
* Change default method
* Remove method (if allowed)

---

## 🔁 SYSTEM ACTIONS

* Securely store payment identifiers
* Link methods to user account
* Validate M-Pesa integration

---

# 🧠 CORE CONCEPT OF WALLET STACK

This is NOT a bank account.

It is:

> 🧠 **A mirror of all economic activity inside your platform**

---

# 🧭 WALLET FLOW IN SYSTEM

```text id="wallet_flow_1"
PaymentFlowScreen
   ↓
TRX CREATED
   ↓
Wallet updates:
   - balance updated
   - transaction logged
   ↓
WalletHomeScreen reflects changes
```

---

# 💡 UX PRINCIPLES

## 1. TRUST FIRST

User must always feel:

* “my money is accounted for”

---

## 2. REAL-TIME UPDATES

Wallet changes instantly after TRX events

---

## 3. SIMPLE FINANCIAL LANGUAGE

Avoid complexity like banking jargon

---

## 4. TRANSPARENCY OF FEES

Always show:

* what was charged
* why it was charged

---

# 👤 CUSTOMER APP — PROFILE STACK


> 🧠 **How the system understands, trusts, and personalizes the user**

---

# 🎯 PURPOSE

> Store user identity, behavior history, preferences, and system settings.

This stack influences:

* vendor ranking
* personalization
* trust scoring
* recommendations
* support experience

---

# 🧭 STACK STRUCTURE

```text id="profile_stack_1"
ProfileStack
├── ProfileScreen
├── SettingsScreen
├── NotificationsScreen
```

---

# 📱 1. PROFILE SCREEN

## 🎯 PURPOSE

Show user identity + activity footprint

---

## 🧩 UI STRUCTURE

```text id="ps_ui_1"
[User Header]
- Name
- Phone / ID
- Location (optional)
- Member since

────────────────────

[TRUST SNAPSHOT]
- Completed Orders: X
- Cancel Rate: Y%
- Preferred vendors: Z

────────────────────

[ACTIVITY SUMMARY]
- Most ordered category
- Most visited vendors
- Events attended

────────────────────

[SHORTCUTS]
- Wallet
- Orders
- Settings
```

---

## 🧠 INTERACTIONS

* Tap trust metrics → detailed breakdown
* Tap orders → OrdersStack
* Tap wallet → WalletStack

---

## 🔁 SYSTEM ACTIONS

* Aggregate:

  * TRX history
  * behavioral patterns
  * engagement signals

---

# 📱 2. SETTINGS SCREEN

## 🎯 PURPOSE

Control system behavior and preferences

---

## 🧩 UI STRUCTURE

```text id="set_ui_1"
[ACCOUNT SETTINGS]
- Edit Profile
- Phone Number
- Location Settings

────────────────────

[PREFERENCES]
- Delivery preference default
- Language
- Notification frequency

────────────────────

[PRIVACY]
- Data visibility controls
- Location sharing toggle

────────────────────

[SUPPORT]
- Help Center
- Contact Support
- Report Issue

────────────────────

[ACCOUNT ACTIONS]
- Logout
- Delete Account
```

---

## 🧠 INTERACTIONS

* Toggle preferences
* Update profile info
* Access support flows

---

## 🔁 SYSTEM ACTIONS

* Update user metadata
* Sync preferences to recommendation engine

---

# 📱 3. NOTIFICATIONS SCREEN

## 🎯 PURPOSE

Central communication hub for all system events

---

## 🧩 UI STRUCTURE

```text id="notif_ui_1"
[Notification Groups]

🔵 Orders
- Order confirmed
- Rider assigned
- Delivery completed

🟢 Payments
- Payment successful
- Refund processed

🟣 Events
- Event reminders
- New nearby events

🟠 System
- Updates
- Promotions
```

---

## 🧠 INTERACTIONS

* Tap notification → deep link into:

  * OrderDetailScreen
  * EventDetailScreen
  * WalletScreen

---

## 🔁 SYSTEM ACTIONS

* Subscribe to:

  * TRX state changes
  * rider updates
  * vendor updates
  * event triggers

---

# 🧠 CORE CONCEPT OF PROFILE STACK

> 🧠 **A living behavioral profile engine**

---

# 🧭 HOW PROFILE CONNECTS TO SYSTEM

```text id="profile_flow_1"
User behavior (orders, searches, events)
        ↓
Profile engine updates:
- trust score
- preferences
- ranking weight
        ↓
Affects:
- vendor ranking
- recommendations
- event visibility
```

---

# 💡 UX PRINCIPLES

## 1. USER MUST FEEL CONTROL

Everything about them is editable or explainable

---

## 2. TRUST IS VISIBLE

Users can see how system “sees them”

---

## 3. NO BLACK BOX

Why something is recommended should be understandable

---

## 4. SIMPLE LANGUAGE

Avoid technical terms like “score” → use:

* reliability
* activity level
* preference match

---
# 🏪 VENDOR APP — DASHBOARD STACK


> 🧠 **Real-time demand, revenue, and activity control panel**

---

# 🎯 PURPOSE

> Give vendors immediate clarity on:

* what is selling
* what is being requested
* what needs attention right now
* how much money is flowing

---

# 🧭 STACK STRUCTURE

```text id="vendor_dashboard_stack_1"
DashboardStack
├── VendorDashboardScreen
├── AnalyticsScreen
```

---

# 📱 1. VENDOR DASHBOARD SCREEN

## 🎯 PURPOSE

Daily operational snapshot (live business state)

---

## 🧩 UI STRUCTURE

```text id="vd_ui_1"
[TOP SUMMARY CARDS]

┌──────────────┐ ┌──────────────┐
│ Today's Sales│ │ Active Orders │
│   12,500 KES │ │       7       │
└──────────────┘ └──────────────┘

┌──────────────┐ ┌──────────────┐
│ Requests     │ │ Stock Alerts │
│      5       │ │      3       │
└──────────────┘ └──────────────┘

────────────────────

[REAL-TIME REQUEST FEED]

- “iPhone charger requested nearby”
- “Order waiting approval”
- “Delivery assigned”

────────────────────

[QUICK ACTIONS]

- Open Requests Inbox
- Add Inventory Item
- View Orders
- Mark Availability

────────────────────

[TRENDING PRODUCTS]

- What customers are searching for
- High demand items nearby
```

---

## 🧠 INTERACTIONS

* Tap request → OrdersStack (RequestInboxScreen)
* Tap product trend → InventoryStack
* Tap alert → direct action (low stock / urgent order)

---

## 🔁 SYSTEM ACTIONS

* Pull live TRX data for vendor
* Aggregate:

  * active requests
  * inventory status
  * sales velocity
* Update demand signals in real-time

---

# 📱 2. ANALYTICS SCREEN

## 🎯 PURPOSE

Deep performance intelligence layer

---

## 🧩 UI STRUCTURE

```text id="va_ui_1"
[DATE FILTER]
- Today / Week / Month

────────────────────

[REVENUE GRAPH]
- Sales over time

────────────────────

[TOP PRODUCTS]
- Highest selling items
- Revenue contribution

────────────────────

[DEMAND INSIGHTS]
- Most searched products not in stock
- Missed opportunities

────────────────────

[FULFILLMENT METRICS]
- Avg response time
- Order acceptance rate
- Delivery completion rate

────────────────────

[COMPARISON]
- This week vs last week
```

---

## 🧠 INTERACTIONS

* Tap product → Inventory detail
* Tap metric → drill-down breakdown
* Filter analytics timeframe

---

## 🔁 SYSTEM ACTIONS

* Aggregate historical TRX data
* Compute:

  * revenue trends
  * conversion rates
  * demand gaps
* Feed insights back into discovery system

---

# 🧠 CORE CONCEPT OF DASHBOARD STACK

> 🧠 **Live business intelligence engine for vendors**

---

# 🧭 HOW DASHBOARD CONNECTS TO SYSTEM

```text id="vendor_dash_flow_1"
Customer demand (search + orders)
        ↓
Vendor receives requests (real-time)
        ↓
Dashboard updates instantly
        ↓
Vendor reacts:
- accept order
- update stock
- adjust pricing
        ↓
System learns demand patterns
```

---

# 💡 UX PRINCIPLES

## 1. REAL-TIME FIRST

Everything must feel live, not static reports

---

## 2. ACTION-ORIENTED DATA

Every metric must lead to a decision

---

## 3. SIMPLICITY UNDER PRESSURE

Vendors should understand everything in <5 seconds

---

## 4. DEMAND OVER REPORTING

Focus on:

* what customers want NOW
  not what happened last month

---
# 📦 VENDOR APP — INVENTORY STACK 

This is the **source of truth for everything the vendor can sell or deliver**.

It is NOT a catalog.

It is:

> 🧠 **A live supply control system connected directly to demand**

---

# 🎯 PURPOSE

> Let vendors create, update, and control what the system can sell, match, and request.

Everything here directly powers:

* customer discovery
* search results
* vendor matching
* order creation

---

# 🧭 STACK STRUCTURE

```text id="vendor_inventory_stack_1"
InventoryStack
├── InventoryListScreen
├── AddProductScreen
├── AddServiceScreen
├── EditItemScreen
```

---

# 📱 1. INVENTORY LIST SCREEN

## 🎯 PURPOSE

Show everything the vendor can offer (products + services)

---

## 🧩 UI STRUCTURE

```text id="vi_ui_1"
[TOP FILTERS]
- All
- Products
- Services
- Low stock
- Out of stock

────────────────────

[INVENTORY ITEMS]

┌────────────────────────────┐
│ Item Name                 │
│ Type: Product / Service   │
│ Price                     │
│ Availability: In stock    │
│ Demand: 🔥 High / Medium  │
│                            │
│ [Edit]  [Toggle Status]   │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap item → EditItemScreen
* Toggle availability → instantly affects customer search
* Filter inventory type

---

## 🔁 SYSTEM ACTIONS

* Sync inventory with:

  * customer search system
  * vendor dashboard demand signals
* Update real-time availability

---

# 📱 2. ADD PRODUCT SCREEN

## 🎯 PURPOSE

Create a sellable physical item

---

## 🧩 UI STRUCTURE

```text id="ap_ui_1"
[PRODUCT DETAILS]

- Product Name
- Category
- Price
- Description

────────────────────

[AVAILABILITY]

- In stock toggle
- Quantity (optional)

────────────────────

[VISIBILITY SETTINGS]

- Visible to all users
- Event-only visibility (optional)

────────────────────

[CONFIRM BUTTON]
→ “Add Product”
```

---

## 🧠 INTERACTIONS

* Create product entry
* Publish to discovery system
* Immediately searchable by customers

---

## 🔁 SYSTEM ACTIONS

* Register product in global catalog
* Attach vendor ID
* Index for search + recommendation engine

---

# 📱 3. ADD SERVICE SCREEN

## 🎯 PURPOSE

Define services the vendor can perform

---

## 🧩 UI STRUCTURE

```text id="as_ui_1"
[SERVICE DETAILS]

- Service Name
- Category (e.g. barber, repair)
- Base Price

────────────────────

[SERVICE MODES]

✔ In-shop
✔ Mobile (I go to customer)
✔ Pickup supported (via rider)

────────────────────

[AVAILABILITY]

- Active / Inactive toggle
- Working hours (optional)

────────────────────

[CONFIRM BUTTON]
→ “Add Service”
```

---

## 🧠 INTERACTIONS

* Define service capability
* Enable service discovery
* Control logistics behavior (VERY IMPORTANT)

---

## 🔁 SYSTEM ACTIONS

* Register service in global service graph
* Link fulfillment modes (A/B/C system)
* Enable matching in service discovery engine

---

# 📱 4. EDIT ITEM SCREEN

## 🎯 PURPOSE

Modify existing product/service dynamically

---

## 🧩 UI STRUCTURE

```text id="ei_ui_1"
[ITEM OVERVIEW]

- Name
- Price
- Availability

────────────────────

[EDIT OPTIONS]

- Update price
- Change stock
- Enable/disable visibility
- Switch service modes (if service)

────────────────────

[DANGER ZONE]

- Delete item
```

---

## 🧠 INTERACTIONS

* Update inventory instantly reflects in customer app
* Disable item removes it from search immediately

---

## 🔁 SYSTEM ACTIONS

* Real-time sync with:

  * search engine
  * order system
  * recommendation engine

---

# 🧠 CORE CONCEPT OF INVENTORY STACK

> 🧠 **Live supply graph feeding the entire marketplace system**

---

# 🧭 HOW INVENTORY CONNECTS TO SYSTEM

```text id="inventory_flow_1"
Vendor creates product/service
        ↓
System indexes it instantly
        ↓
Customer searches → sees item
        ↓
Customer selects → TRX created
        ↓
Vendor receives request
```

---

# 💡 UX PRINCIPLES

## 1. INSTANT VISIBILITY

Any change affects customers immediately

---

## 2. MINIMAL INPUT

Vendors should create items in <30 seconds

---

## 3. SUPPLY = SIGNAL

Inventory is not static — it drives demand matching

---

# 📥 VENDOR APP — ORDERS STACK 

This is the **execution core of the vendor system**.

It is NOT “order management”.

It is:

> 🧠 **A live request-to-fulfillment decision engine**

---

# 🎯 PURPOSE

> Let vendors receive, evaluate, accept, and fulfill customer demand in real time.

This stack handles:

* product requests (A flow)
* service requests (B flow)
* event-driven demand (C flow)
* rider coordination (if needed)

---

# 🧭 STACK STRUCTURE

```text id="vendor_orders_stack_1"
OrdersStack
├── RequestInboxScreen
├── OrderDetailScreen
├── FulfillmentCenterScreen
```

---

# 📱 1. REQUEST INBOX SCREEN

## 🎯 PURPOSE

Central “incoming demand feed” for vendor

---

## 🧩 UI STRUCTURE

```text id="vo_ui_1"
[REQUEST FILTERS]
- All
- Products
- Services
- Urgent
- Delivery required

────────────────────

[REQUEST CARDS]

┌────────────────────────────┐
│ Product/Service Requested  │
│ Customer distance          │
│ Quantity / details         │
│ Fulfillment type           │
│                            │
│ [ACCEPT] [REJECT]          │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap request → OrderDetailScreen
* Accept → moves to FulfillmentCenterScreen
* Reject → removes request (or logs decline reason)

---

## 🔁 SYSTEM ACTIONS

* Pull TRX requests assigned to vendor
* Sort by:

  * urgency
  * proximity
  * availability match

---

# 📱 2. ORDER DETAIL SCREEN (VENDOR VIEW)

## 🎯 PURPOSE

Show full context before decision

---

## 🧩 UI STRUCTURE

```text id="vod_ui_1"
[REQUEST SUMMARY]

- Item / Service
- Customer location
- Price
- Fulfillment type (VERY IMPORTANT)

────────────────────

[CUSTOMER INFO]
- Distance
- Trust score (optional)
- Order history snippet

────────────────────

[FULFILLMENT MODE]

- 🏪 Walk-in
- 🛵 Delivery
- 🧑‍🔧 Mobile service
- 📦 Pickup via rider

────────────────────

[ACTION BUTTONS]

[ACCEPT REQUEST]
[MODIFY (optional)]
[REJECT REQUEST]
```

---

## 🧠 INTERACTIONS

* Accept → moves to fulfillment pipeline
* Modify → adjust availability, price, or timing
* Reject → logs reason for system learning

---

## 🔁 SYSTEM ACTIONS

* Lock inventory (if product)
* Assign fulfillment route
* Notify customer instantly

---

# 📱 3. FULFILLMENT CENTER SCREEN

## 🎯 PURPOSE

Execution hub once vendor accepts request

---

## 🧩 UI STRUCTURE

```text id="vfc_ui_1"
[ORDER STATUS HEADER]

- Status: Preparing / Ready / Waiting Rider

────────────────────

[FULFILLMENT TYPE]

If WALK-IN:
→ “Customer is coming”

If DELIVERY:
→ “Rider assigned”

If MOBILE SERVICE:
→ “En route to customer”

If PICKUP:
→ “Awaiting rider pickup”

────────────────────

[ORDER ACTIONS]

- Mark Ready
- Update Status
- Contact Rider
- Contact Customer
```

---

## 🧠 INTERACTIONS

* Update fulfillment state
* Trigger rider assignment (if needed)
* Notify customer in real time

---

## 🔁 SYSTEM ACTIONS

* Update TRX lifecycle state:

  * CONFIRMED → PREPARING → READY → IN_TRANSIT
* Sync with RiderApp (if logistics involved)

---

# 🧠 CORE CONCEPT OF VENDOR ORDERS STACK

> 🧠 **Decision + execution control layer for supply side**

---

# 🧭 HOW IT CONNECTS TO SYSTEM

```text id="vendor_orders_flow_1"
Customer request (TRX created)
        ↓
RequestInboxScreen
        ↓
Vendor decision:
   ACCEPT / REJECT / MODIFY
        ↓
FulfillmentCenterScreen
        ↓
Rider assignment (if needed)
        ↓
Customer tracking begins
```

---

# 💡 UX PRINCIPLES

## 1. SPEED IS EVERYTHING

Vendor decisions must take seconds, not minutes

---

## 2. CLEAR FULFILLMENT CONTEXT

Every request must show:

* how delivery happens
* who moves
* what is expected

---

## 3. MINIMAL FRICTION

Accept / reject must be 1 tap actions

---

## 4. NO AMBIGUITY

Vendor should never guess logistics — system tells them

---
# 🎪 VENDOR APP — EVENTS STACK 

This is where your platform stops being a marketplace and becomes a **demand accelerator**.

It is NOT event listings.

It is:

> 🧠 **A temporary high-density commerce environment (sales + services + visibility boost)**

---

# 🎯 PURPOSE

> Let vendors join, manage, and profit from event-driven demand spikes.

Events act as:

* traffic boosters
* sales multipliers
* discovery engines
* logistics hotspots

---

# 🧭 STACK STRUCTURE

```text id="vendor_events_stack_1"
EventsStack
├── EventListScreen
├── EventDetailScreen
├── ParticipationScreen
```

---

# 📱 1. EVENT LIST SCREEN

## 🎯 PURPOSE

Show available and active events vendors can join

---

## 🧩 UI STRUCTURE

```text id="ve_ui_1"
[EVENT FILTERS]
- Upcoming
- Active
- Nearby
- High Traffic

────────────────────

[EVENT CARDS]

┌────────────────────────────┐
│ Event Name                │
│ Location                  │
│ Date / Live status       │
│ Expected traffic: 🔥 High │
│                            │
│ [View] [Join Event]       │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap event → EventDetailScreen
* Join event → ParticipationScreen
* Filter events by demand level

---

## 🔁 SYSTEM ACTIONS

* Pull event feed from global system
* Rank events by:

  * foot traffic
  * category match
  * vendor relevance

---

# 📱 2. EVENT DETAIL SCREEN

## 🎯 PURPOSE

Show full event opportunity before vendor joins

---

## 🧩 UI STRUCTURE

```text id="ved_ui_1"
[EVENT OVERVIEW]

- Event name
- Location
- Time
- Duration

────────────────────

[DEMAND PREVIEW]

- Expected visitors
- Trending categories
- Popular search terms

────────────────────

[EVENT MARKET LAYER]

- Products in demand
- Services in demand
- Competitor vendors

────────────────────

[ACTION]

[JOIN EVENT]
[VIEW REQUIREMENTS]
```

---

## 🧠 INTERACTIONS

* View demand insights
* Preview competition
* Join event participation flow

---

## 🔁 SYSTEM ACTIONS

* Aggregate demand predictions
* Match vendor inventory/services with event demand graph

---

# 📱 3. PARTICIPATION SCREEN

## 🎯 PURPOSE

Control vendor presence inside an event

---

## 🧩 UI STRUCTURE

```text id="vp_ui_1"
[PARTICIPATION STATUS]

- Status: Joined / Active / Pending

────────────────────

[LINK INVENTORY]

- Select products to feature
- Select services to promote

────────────────────

[PRICING OPTIONS]

- Standard pricing
- Event discount mode
- Flash deals toggle

────────────────────

[VISIBILITY BOOST]

- Featured placement (optional)
- Priority listing

────────────────────

[ACTIVATE PARTICIPATION]
```

---

## 🧠 INTERACTIONS

* Select inventory items to push into event
* Adjust pricing for event demand
* Activate event visibility mode

---

## 🔁 SYSTEM ACTIONS

* Sync selected inventory with event marketplace layer
* Boost ranking in event search
* Enable high-frequency request routing

---

# 🧠 CORE CONCEPT OF EVENTS STACK

> 🧠 **A demand multiplier engine for the entire ecosystem**

---

# 🧭 HOW EVENTS CONNECT TO SYSTEM

```text id="vendor_events_flow_1"
Event created in system
        ↓
Vendor joins event
        ↓
Inventory/services linked to event
        ↓
Customer enters event marketplace
        ↓
High-density requests generated
        ↓
OrdersStack + Rider system activated heavily
```

---

# 💡 UX PRINCIPLES

## 1. EVENTS = OPPORTUNITY ZONES

Vendors should feel:

> “I make more money here than normal days”

---

## 2. FAST PARTICIPATION

Joining an event should take <1 minute

---

## 3. DEMAND VISIBILITY FIRST

Show what will SELL before showing logistics

---

## 4. FLEXIBLE PRICING CONTROL

Vendors must adjust pricing per event

---
# 👤 VENDOR APP — PROFILE STACK 

> 🧠 **The vendor’s public reputation + internal control center**

---

# 🎯 PURPOSE

> Define who the vendor is, how trustworthy they are, and how the system ranks them.

This directly affects:

* customer decisions
* search ranking
* request volume
* event selection priority

---

# 🧭 STACK STRUCTURE

```text id="vendor_profile_stack_1"
ProfileStack
├── VendorProfileScreen
├── RatingsScreen
├── SettingsScreen
```

---

# 📱 1. VENDOR PROFILE SCREEN

## 🎯 PURPOSE

Show business identity + performance snapshot

---

## 🧩 UI STRUCTURE

```text id="vp_ui_1"
[BUSINESS HEADER]

- Store Name
- Category (electronics, food, etc.)
- Location
- Open / Closed status

────────────────────

[TRUST SNAPSHOT]

- Rating (⭐ 4.6)
- Completed Orders
- Response Time
- Acceptance Rate

────────────────────

[BUSINESS STATS]

- Total revenue (optional internal)
- Active listings
- Event participation count

────────────────────

[SHORTCUTS]

- View Ratings
- Edit Profile
- Open Inventory
```

---

## 🧠 INTERACTIONS

* Tap rating → RatingsScreen
* Tap inventory → InventoryStack
* Toggle store open/closed status

---

## 🔁 SYSTEM ACTIONS

* Aggregate:

  * TRX completion data
  * response times
  * customer feedback

---

# 📱 2. RATINGS SCREEN

## 🎯 PURPOSE

Show customer feedback + reputation signals

---

## 🧩 UI STRUCTURE

```text id="vr_ui_1"
[OVERALL RATING]

⭐ 4.6 / 5
Based on 120 reviews

────────────────────

[RATING BREAKDOWN]

- 5★: ████████
- 4★: ████
- 3★: ██
- 2★: █
- 1★: █

────────────────────

[REVIEWS LIST]

┌────────────────────────────┐
│ ⭐⭐⭐⭐⭐                    │
│ “Fast delivery, good item”│
│ Date                      │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Scroll reviews
* Filter by rating
* Respond to reviews (future phase)

---

## 🔁 SYSTEM ACTIONS

* Pull feedback from completed TRX
* Aggregate into rating metrics

---

# 📱 3. SETTINGS SCREEN (VENDOR)

## 🎯 PURPOSE

Control business configuration

---

## 🧩 UI STRUCTURE

```text id="vs_ui_1"
[BUSINESS SETTINGS]

- Store Name
- Category
- Location radius

────────────────────

[OPERATIONS]

- Open / Close store
- Default fulfillment mode
- Working hours

────────────────────

[PAYMENTS]

- M-Pesa number
- Payout preferences

────────────────────

[SUPPORT]

- Help Center
- Contact Support

────────────────────

[ACCOUNT ACTIONS]

- Logout
```

---

## 🧠 INTERACTIONS

* Update store details
* Adjust operational settings
* Manage payout info

---

## 🔁 SYSTEM ACTIONS

* Sync vendor settings with:

  * discovery engine
  * order routing system
  * payment system

---

# 🧠 CORE CONCEPT OF VENDOR PROFILE STACK

This is NOT a static business page.

It is:

> 🧠 **A dynamic trust and ranking engine**

---

# 🧭 HOW PROFILE AFFECTS SYSTEM

```text id="vendor_profile_flow_1"
Vendor actions (accept orders, fulfill, respond fast)
        ↓
System updates trust metrics
        ↓
Affects:
- ranking in search
- request frequency
- event invitations
```

---

# 💡 UX PRINCIPLES

## 1. TRUST IS VISIBLE

Customers must clearly see:

* reliability
* responsiveness
* quality

---

## 2. PERFORMANCE DRIVEN

Vendor success depends on behavior, not just inventory

---

## 3. SIMPLE CONTROL

Settings should be easy to change quickly

---

## 4. FEEDBACK LOOP

Reviews directly impact vendor success

---

# 🛵 RIDER APP — HOME STACK 


> 🧠 **Real-time participation control in the logistics network**

---

# 🎯 PURPOSE

> Let riders control when they are available to receive jobs and see their current operational state.

Everything starts here:

* no availability → no jobs
* availability → job feed activates

---

# 🧭 STACK STRUCTURE

```text id="rider_home_stack_1"
HomeStack
├── RiderHomeScreen
├── AvailabilityToggleScreen
```

---

# 📱 1. RIDER HOME SCREEN

## 🎯 PURPOSE

Show current status + quick operational overview

---

## 🧩 UI STRUCTURE

```text id="rh_ui_1"
[STATUS HEADER]

🟢 Online / 🔴 Offline

────────────────────

[EARNINGS SNAPSHOT]

- Today’s earnings
- Completed jobs
- Pending payouts

────────────────────

[QUICK ACTION]

[GO ONLINE] / [GO OFFLINE]

────────────────────

[CURRENT STATE]

If Offline:
→ “You are not receiving jobs”

If Online:
→ “Waiting for jobs…”

If Active Job:
→ “You have an ongoing job”
→ [Go to Navigation]

────────────────────

[HOT ZONES (OPTIONAL)]

- Areas with high demand nearby
```

---

## 🧠 INTERACTIONS

* Tap “Go Online” → AvailabilityToggleScreen
* Tap “Go Offline” → confirm action
* Tap active job → NavigationStack

---

## 🔁 SYSTEM ACTIONS

* Check rider availability state
* Pull basic stats (earnings, jobs)
* Listen for job assignment triggers

---

# 📱 2. AVAILABILITY TOGGLE SCREEN

## 🎯 PURPOSE

Explicitly control rider availability with clarity

---

## 🧩 UI STRUCTURE

```text id="rat_ui_1"
[TOGGLE CONTROL]

🔴 Offline  ← →  🟢 Online

────────────────────

[STATUS EXPLANATION]

If Offline:
→ “You will not receive any jobs”

If Online:
→ “You will receive delivery and ride requests”

────────────────────

[CONFIRMATION BUTTON]

[CONFIRM STATUS CHANGE]
```

---

## 🧠 INTERACTIONS

* Toggle availability state
* Confirm status change

---

## 🔁 SYSTEM ACTIONS

When going ONLINE:

```text id="rat_sys_1"
1. Register rider in job matching system
2. Enable job feed
3. Start listening for assignments
```

---

When going OFFLINE:

```text id="rat_sys_2"
1. Remove rider from matching pool
2. Stop job notifications
3. Preserve current job (if active)
```

---

# 🧠 CORE CONCEPT OF HOME STACK


> 🧠 **A real-time participation gateway to the logistics economy**

---

# 🧭 HOW IT CONNECTS TO SYSTEM

```text id="rider_home_flow_1"
Rider goes ONLINE
        ↓
System adds rider to matching pool
        ↓
Vendor confirms order (delivery required)
        ↓
Job created
        ↓
Rider receives job in JobsStack
```

---

# 💡 UX PRINCIPLES

## 1. ABSOLUTE CLARITY

Rider must always know:

* am I working or not?

---

## 2. ZERO CONFUSION

Online = jobs will come
Offline = nothing will come

---

## 3. INSTANT RESPONSE

Status change must reflect immediately

---

## 4. LOW FRICTION

1 tap to go online/offline

---
# 📦 RIDER APP — JOBS STACK (JOB INTAKE + DECISION ENGINE)

> 🧠 **“Here is the opportunity — do you take it or not?”**

---

# 🎯 PURPOSE

> Deliver clear, actionable jobs to riders with zero ambiguity so they can accept and execute quickly.

This stack handles:

* delivery jobs (products/events)
* service logistics (item pickup)
* ride jobs (customer transport)

---

# 🧭 STACK STRUCTURE

```text id="rider_jobs_stack_1"
JobsStack
├── JobFeedScreen
├── JobDetailScreen
├── AcceptRejectScreen
```

---

# 📱 1. JOB FEED SCREEN

## 🎯 PURPOSE

Show available jobs in real time

---

## 🧩 UI STRUCTURE

```text id="rj_ui_1"
[JOB FILTERS]

- All
- 🚗 Ride Jobs
- 📦 Delivery Jobs
- Nearby
- High Pay

────────────────────

[JOB CARDS]

┌────────────────────────────┐
│ Job Type: Delivery         │
│ Pickup: Vendor location    │
│ Drop-off: Customer         │
│ Distance: 3.2 km           │
│ Earnings: 250 KES          │
│                            │
│ [View Details]             │
└────────────────────────────┘
```

---

## 🧠 INTERACTIONS

* Tap job → JobDetailScreen
* Filter jobs by type or proximity

---

## 🔁 SYSTEM ACTIONS

* Pull jobs from matching engine
* Rank jobs based on:

  * proximity
  * rider rating
  * availability
* Refresh in real time

---

# 📱 2. JOB DETAIL SCREEN

## 🎯 PURPOSE

Give full clarity before acceptance

---

## 🧩 UI STRUCTURE

```text id="rjd_ui_1"
[JOB OVERVIEW]

- Type: 🚗 Ride / 📦 Delivery
- Earnings
- Estimated duration

────────────────────

[ROUTE PREVIEW]

- Pickup location
- Drop-off location

────────────────────

[ITEM / PASSENGER INFO]

- Item type (if delivery)
- Notes (fragile, urgent, etc.)

────────────────────

[ACTIONS]

[ACCEPT JOB]
[REJECT JOB]
```

---

## 🧠 INTERACTIONS

* Review route + earnings
* Decide quickly

---

## 🔁 SYSTEM ACTIONS

* Lock job temporarily for rider viewing
* Provide estimated metrics (ETA, earnings)

---

# 📱 3. ACCEPT / REJECT SCREEN

## 🎯 PURPOSE

Finalize rider decision with confirmation

---

## 🧩 UI STRUCTURE

```text id="rar_ui_1"
[CONFIRM JOB]

- Earnings summary
- Distance
- Estimated time

────────────────────

[FINAL ACTION]

[CONFIRM ACCEPT]
[DECLINE]
```

---

## 🧠 INTERACTIONS

* Accept → job assigned → move to NavigationStack
* Reject → job released back to pool

---

## 🔁 SYSTEM ACTIONS

When ACCEPTED:

```text id="rar_sys_1"
1. Assign job to rider
2. Lock job (no other rider sees it)
3. Notify vendor + customer
4. Transition to NavigationStack
```

---

When REJECTED:

```text id="rar_sys_2"
1. Return job to pool
2. Re-rank for other riders
```

---

# 🧠 CORE CONCEPT OF JOBS STACK

This is NOT a list.

It is:

> 🧠 **A real-time opportunity marketplace for riders**

---

# 🧭 HOW IT CONNECTS TO SYSTEM

```text id="rider_jobs_flow_1"
Vendor confirms order
        ↓
System creates job
        ↓
Job appears in JobFeedScreen
        ↓
Rider views → accepts
        ↓
Job assigned
        ↓
NavigationStack begins execution
```

---

# 💡 UX PRINCIPLES

## 1. ZERO UNCERTAINTY

Every job must clearly show:

* type
* route
* earnings

---

## 2. FAST DECISION MAKING

Rider should decide in <3 seconds

---

## 3. NO NOISE

Only real, confirmed jobs appear

---

## 4. CLEAR LABELING

Always distinguish:

* 🚗 Transport Person
* 📦 Deliver Item

---
---

# 🧭 RIDER APP — NAVIGATION STACK (REAL-WORLD EXECUTION ENGINE)

> 🧠 **The system enters the real world — movement, delivery, completion**

---

# 🎯 PURPOSE

> Guide the rider through the entire job execution with clarity, tracking, and confirmation.

This stack handles:

* pickup navigation
* delivery navigation
* real-time tracking
* completion confirmation

---

# 🧭 STACK STRUCTURE

```text id="rider_navigation_stack_1"
NavigationStack
├── LiveNavigationScreen
├── DeliveryTrackingScreen
├── CompletionScreen
```

---

# 📱 1. LIVE NAVIGATION SCREEN

## 🎯 PURPOSE

Guide rider step-by-step through route

---

## 🧩 UI STRUCTURE

```text id="rn_ui_1"
[MAP VIEW]

- Rider location (moving)
- Pickup location (vendor / customer)
- Route path

────────────────────

[STEP PANEL]

Step 1: Go to Pickup
→ Vendor / Customer address

Step 2: Deliver to Drop-off
→ Final destination

────────────────────

[ACTIONS]

[ARRIVED AT PICKUP]
[START DELIVERY]
```

---

## 🧠 INTERACTIONS

* Follow GPS route
* Tap “Arrived at Pickup”
* Transition to next step

---

## 🔁 SYSTEM ACTIONS

* Stream rider GPS
* Update ETA dynamically
* Notify:

  * vendor (rider arriving)
  * customer (rider en route)

---

# 📱 2. DELIVERY TRACKING SCREEN

## 🎯 PURPOSE

Show active delivery state + coordination tools

---

## 🧩 UI STRUCTURE

```text id="rdt_ui_1"
[STATUS HEADER]

- Status: Picked up / In transit / Arriving

────────────────────

[MAP VIEW]

- Rider moving toward drop-off
- Customer location

────────────────────

[INFO PANEL]

- Customer / Vendor name
- Contact buttons

────────────────────

[ACTIONS]

[CALL]
[CHAT]
[CONFIRM ARRIVAL]
```

---

## 🧠 INTERACTIONS

* Call customer/vendor
* Confirm arrival
* Track movement

---

## 🔁 SYSTEM ACTIONS

* Sync live GPS
* Push updates to:

  * Customer (OrderTrackingScreen)
  * Vendor (FulfillmentCenter)

---

# 📱 3. COMPLETION SCREEN

## 🎯 PURPOSE

Finalize job and trigger payout

---

## 🧩 UI STRUCTURE

```text id="rc_ui_1"
[JOB SUMMARY]

- Job type
- Distance covered
- Earnings

────────────────────

[CONFIRMATION]

“Mark this job as completed?”

────────────────────

[ACTIONS]

[COMPLETE JOB]
```

---

## 🧠 INTERACTIONS

* Confirm job completion
* Trigger earnings update

---

## 🔁 SYSTEM ACTIONS

```text id="rc_sys_1"
1. Mark TRX as COMPLETED
2. Update:
   - rider earnings
   - vendor completion
   - customer order status
3. Trigger wallet updates
4. Release rider to job pool
```

---

# 🧠 CORE CONCEPT OF NAVIGATION STACK

This is NOT maps.

It is:

> 🧠 **Execution layer where digital intent becomes physical fulfillment**

---

# 🧭 FULL EXECUTION FLOW

```text id="rider_nav_flow_1"
Job accepted
        ↓
LiveNavigationScreen (go to pickup)
        ↓
Confirm pickup
        ↓
DeliveryTrackingScreen (in transit)
        ↓
Arrival at destination
        ↓
CompletionScreen
        ↓
TRX COMPLETED
```

---

# 💡 UX PRINCIPLES

## 1. STEP-BY-STEP CLARITY

Rider should always know:

* where to go
* what to do next

---

## 2. REAL-TIME FEEDBACK

Every movement updates:

* customer
* vendor
* system

---

## 3. MINIMAL DISTRACTION

No unnecessary UI — focus on movement

---

## 4. CONFIRMATION-BASED FLOW

Every step must be explicitly confirmed

---
# 💰 RIDER APP — EARNINGS STACK (FINANCIAL CONTROL LAYER)

> 🧠 **“How much have I made, and how do I get it?”**

If this is unclear → riders lose trust → system breaks.

---

# 🎯 PURPOSE

> Give riders **full visibility, control, and trust** over their earnings, payouts, and obligations.

This stack connects directly to your **ledger system**:

* earnings (what they made)
* payouts (what they can withdraw)
* debts (cash jobs → what they owe platform)

---

# 🧭 STACK STRUCTURE

```text id="rider_earnings_stack_1"
EarningsStack
├── EarningsOverviewScreen
├── WithdrawalsScreen
├── EarningsHistoryScreen
```

---

# 📱 1. EARNINGS OVERVIEW SCREEN

## 🎯 PURPOSE

Quick financial snapshot

---

## 🧩 UI STRUCTURE

```text id="re_ui_1"
[BALANCE SUMMARY]

Available Balance: 3,250 KES
Pending Earnings: 1,200 KES
Owed to Platform: -450 KES

────────────────────

[TODAY]

- Jobs completed: 6
- Earnings today: 1,800 KES

────────────────────

[QUICK ACTIONS]

[Withdraw Money]
[View History]

────────────────────

[INSIGHTS]

- “You earned more than yesterday”
- “High demand in your area”
```

---

## 🧠 INTERACTIONS

* Tap withdraw → WithdrawalsScreen
* Tap history → EarningsHistoryScreen

---

## 🔁 SYSTEM ACTIONS

* Pull from rider ledger:

  * available balance
  * pending
  * debt (cash jobs)
* Update in real time

---

# 📱 2. WITHDRAWALS SCREEN

## 🎯 PURPOSE

Let rider convert earnings → real money

---

## 🧩 UI STRUCTURE

```text id="rw_ui_1"
[WITHDRAWABLE BALANCE]

2,800 KES

────────────────────

[WITHDRAW METHOD]

- M-Pesa (primary)
- (Future: bank)

────────────────────

[INPUT]

Enter amount

────────────────────

[FEE / BREAKDOWN]

- Withdrawal fee (if any)
- Remaining balance

────────────────────

[ACTION]

[CONFIRM WITHDRAWAL]
```

---

## 🧠 INTERACTIONS

* Enter amount
* Confirm withdrawal

---

## 🔁 SYSTEM ACTIONS

```text id="rw_sys_1"
1. Validate balance
2. Check outstanding debt
3. Deduct amount
4. Trigger M-Pesa payout
5. Update ledger
```

---

## ⚠️ IMPORTANT LOGIC

If rider owes platform (cash jobs):

```text id="rw_sys_2"
Available = Earnings - Debt
```

👉 System must clearly show:

> “You owe platform X KES from cash jobs”

---

# 📱 3. EARNINGS HISTORY SCREEN

## 🎯 PURPOSE

Full transparency of all transactions

---

## 🧩 UI STRUCTURE

```text id="reh_ui_1"
[TRANSACTION LIST]

┌────────────────────────────┐
│ Delivery Job              │
│ +250 KES                  │
│ Status: Completed         │
│ Date: Today               │
└────────────────────────────┘

┌────────────────────────────┐
│ Cash Job Adjustment       │
│ -50 KES (Platform fee)    │
│ Status: Pending settlement│
└────────────────────────────┘

────────────────────

[FILTERS]

- All
- Jobs
- Withdrawals
- Adjustments
```

---

## 🧠 INTERACTIONS

* View breakdown of each transaction
* Filter by type

---

## 🔁 SYSTEM ACTIONS

* Pull all ledger entries:

  * job earnings
  * withdrawals
  * platform deductions
* Display clearly

---

# 🧠 CORE CONCEPT OF EARNINGS STACK

This is NOT just a wallet.

It is:

> 🧠 **A transparent financial ledger for rider trust and retention**

---

# 🧭 HOW IT CONNECTS TO SYSTEM

```text id="rider_earnings_flow_1"
Job completed
        ↓
System updates TRX
        ↓
Ledger updated:
  - rider earnings
  - platform fee
        ↓
EarningsOverview reflects change
        ↓
Rider withdraws via M-Pesa
```

---

# 💡 UX PRINCIPLES

## 1. FULL TRANSPARENCY

Rider must always see:

* what they earned
* what they owe
* what they can withdraw

---

## 2. NO HIDDEN DEDUCTIONS

Every deduction must be explained

---

## 3. FAST CASH ACCESS

Withdrawal should feel immediate

---

## 4. TRUST FIRST

This screen builds long-term retention

---
# 👤 RIDER APP — PROFILE STACK 

> 🧠 **“Who am I in this system, and how do I control my experience?”**

---

# 🎯 PURPOSE

> Give riders control over their identity, preferences, and system-level settings while reinforcing trust.

---

# 🧭 STACK STRUCTURE

```text id="rider_profile_stack_1"
ProfileStack
├── RiderProfileScreen
├── SettingsScreen
```

---

# 📱 1. RIDER PROFILE SCREEN

## 🎯 PURPOSE

Display rider identity + performance signals

---

## 🧩 UI STRUCTURE

```text id="rp_ui_1"
[PROFILE HEADER]

- Profile picture
- Name
- Phone number

────────────────────

[PERFORMANCE]

- Rating ⭐ 4.8
- Total jobs completed
- On-time delivery %

────────────────────

[STATUS]

- Current state: Online / Offline

────────────────────

[QUICK LINKS]

- Earnings
- Job History (future expansion)
- Support

────────────────────

[ACTIONS]

[EDIT PROFILE]
```

---

## 🧠 INTERACTIONS

* View performance stats
* Navigate to earnings/support
* Edit profile info

---

## 🔁 SYSTEM ACTIONS

* Pull:

  * rider identity
  * performance metrics
  * ratings
* Update dynamically after each job

---

# 📱 2. SETTINGS SCREEN

## 🎯 PURPOSE

Control system preferences and account-level actions

---

## 🧩 UI STRUCTURE

```text id="rs_ui_1"
[ACCOUNT]

- Edit profile
- Change phone number

────────────────────

[NOTIFICATIONS]

- Job alerts ON/OFF
- Sound / vibration

────────────────────

[PREFERENCES]

- Default navigation app
- Language (future)

────────────────────

[SUPPORT]

- Contact support
- Help center

────────────────────

[SECURITY]

- Logout
```

---

## 🧠 INTERACTIONS

* Toggle notifications
* Update account info
* Access support
* Logout

---

## 🔁 SYSTEM ACTIONS

* Persist settings
* Manage session state (logout)
* Control notification subscriptions

---

# 🧠 CORE CONCEPT OF PROFILE STACK

This is NOT just a profile page.

It is:

> 🧠 **Identity + control + trust anchor for the rider**

---

# 🧭 HOW IT CONNECTS TO SYSTEM

```text id="rider_profile_flow_1"
Job completed
        ↓
Rating updated
        ↓
Profile reflects performance

Settings updated
        ↓
System behavior changes (notifications, etc.)
```

---

# 💡 UX PRINCIPLES

## 1. TRUST VISIBILITY

Rider must see:

* their rating
* their performance

---

## 2. SIMPLE CONTROL

Settings should be:

* minimal
* clear
* actionable

---

## 3. NO CLUTTER

Avoid overloading with unnecessary options

---

## 4. ACCESSIBLE SUPPORT

Help should always be 1–2 taps away

---
# 🌐 GLOBAL MODAL STACK — SYSTEM ENGINE

> 🧠 **The invisible operating system that orchestrates transactions, money, and cross-role coordination**

---

# 🎯 PURPOSE

> Handle **cross-app flows** that cannot belong to any single role (Customer, Vendor, Rider)

This includes:

* 🧾 Order / TRX creation (MOST IMPORTANT)
* 💳 Payment handling (M-Pesa / Cash logic)
* 🔔 Notifications (system-wide)
* 💼 Wallet interactions
* 🆘 Support

---

# 🧭 STACK STRUCTURE

```text id="global_modal_stack_1"
GlobalModalStack
├── PaymentFlowScreen   // CORE ENGINE
├── NotificationsScreen
├── WalletModalScreen
├── SupportScreen
├── SettingsScreen
```

---

# 💥 MOST IMPORTANT: PAYMENT FLOW SCREEN

## 🧠 THIS IS NOT “PAYMENT”

It is:

> 🧠 **Transaction Creation + Orchestration Engine (TRX)**

---

# 📱 1. PAYMENT FLOW SCREEN (ORDER CREATION CORE)

## 🎯 PURPOSE

Turn **user intent** into a structured **transaction (TRX)**

---

## 🧩 TRIGGER POINTS

```text id="pfs_trigger_1"
- ProductDetailScreen
- VendorSelectionScreen
- ServiceDetailScreen
- Event interactions
```

---

## 🧩 UI STRUCTURE

```text id="pfs_ui_1"
[ITEM SUMMARY]

- Product / Service
- Vendor / Provider
- Price

────────────────────

[FULFILLMENT MODE]

- 🏪 Pickup (Go to shop)
- 🛵 Delivery (Rider involved)

────────────────────

[LOCATION]

- Delivery address (if needed)

────────────────────

[PAYMENT METHOD]

- M-Pesa
- Cash

────────────────────

[BREAKDOWN]

- Item price
- Delivery fee (if any)
- Platform fee

────────────────────

[ACTION]

[CONFIRM REQUEST]
```

---

## 🧠 INTERACTIONS

* Choose fulfillment mode
* Choose payment method
* Confirm request

---

## 🔁 SYSTEM ACTIONS (CRITICAL)

When user confirms:

```text id="pfs_sys_1"
1. Create TRX (Transaction Object)

TRX includes:
- customer
- vendor/provider
- rider (optional)
- total amount
- platform fee
- payment method
- fulfillment type

2. Send request to vendor/provider

3. Set status:
→ "REQUESTED"

4. If delivery:
→ prepare rider job (pending vendor acceptance)
```

---

# 💳 PAYMENT LOGIC (BUILT INTO THIS FLOW)

---

## 🟢 M-PESA FLOW

```text id="mpesa_flow_1"
Customer pays digitally
        ↓
Platform receives money
        ↓
Auto-split:
  - Vendor share
  - Rider share
  - Platform fee
```

---

## 💵 CASH FLOW

```text id="cash_flow_1"
Customer pays physically
        ↓
Platform records TRX
        ↓
Ledger updated:
  - Vendor owed
  - Rider owed
  - Platform owed
```

---

# 📱 2. NOTIFICATIONS SCREEN

## 🎯 PURPOSE

Central system alerts

---

## 🧩 UI STRUCTURE

```text id="notif_ui_1"
[NOTIFICATIONS LIST]

- “Vendor accepted your request”
- “Rider is on the way”
- “Order completed”

────────────────────

[FILTERS]

- All
- Orders
- Payments
- System
```

---

## 🔁 SYSTEM ACTIONS

* Aggregate notifications from:

  * orders
  * jobs
  * payments

---

# 📱 3. WALLET MODAL SCREEN

## 🎯 PURPOSE

Quick financial interaction layer

---

## 🧩 UI STRUCTURE

```text id="wallet_ui_1"
[BALANCE]

- Current balance

────────────────────

[ACTIONS]

- Add money
- View transactions

────────────────────

[RECENT ACTIVITY]
```

---

## 🔁 SYSTEM ACTIONS

* Pull wallet data
* Sync with ledger

---

# 📱 4. SUPPORT SCREEN

## 🎯 PURPOSE

Resolve issues across system

---

## 🧩 UI STRUCTURE

```text id="support_ui_1"
[HELP OPTIONS]

- Report issue
- Contact support
- FAQ

────────────────────

[ACTIVE ISSUES]

- Open tickets
```

---

## 🔁 SYSTEM ACTIONS

* Create support tickets
* Link to TRX if needed

---

# 📱 5. SETTINGS SCREEN (GLOBAL)

## 🎯 PURPOSE

Cross-app settings

---

## 🧩 UI STRUCTURE

```text id="global_settings_ui_1"
- Notifications preferences
- Privacy settings
- Account controls
```

---

# 🧠 CORE CONCEPT OF GLOBAL MODAL STACK

This is NOT UI.

It is:

> 🧠 **System-level orchestration layer that sits above all apps**

---

# 🧭 FULL SYSTEM CONNECTION

```text id="global_flow_1"
Customer initiates action
        ↓
PaymentFlowScreen creates TRX
        ↓
Vendor receives request
        ↓
Vendor accepts
        ↓
Rider job created (if needed)
        ↓
Execution (NavigationStack)
        ↓
Completion
        ↓
Ledger + Wallet updated
        ↓
Notifications sent
```

---

# 💡 UX PRINCIPLES

## 1. GLOBAL ACCESS

These screens must be accessible from anywhere

---

## 2. CONSISTENCY

Same behavior across:

* Customer
* Vendor
* Rider

---

## 3. SYSTEM CLARITY

User must understand:

* what’s happening
* what’s next

---

## 4. TRANSACTION VISIBILITY

Every action → tied to a TRX

---
