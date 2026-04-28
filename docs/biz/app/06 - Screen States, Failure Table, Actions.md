
---

# 🧠 HOW TO READ THIS

For each screen:

### 1. States

### 2. What user sees

### 3. What user can do (Buttons)

### 4. Failure Table

### 5. Action Rules

---

# 🔐 1. SPLASH SCREEN

## 1. States

* Loading
* Authenticated
* Not Authenticated
* Error

## 2. What user sees

* Logo
* Loader
* Optional tagline

## 3. Actions

(None — system controlled)

---

## Failure Table

| Scenario        | Message                         | Action            |
| --------------- | ------------------------------- | ----------------- |
| Network failure | "Connection issue. Retrying..." | Auto retry        |
| Token invalid   | (silent)                        | Redirect to Login |
| Server down     | "Something went wrong"          | Retry             |

---

## Action Rules

| State   | Button           |
| ------- | ---------------- |
| Loading | None             |
| Error   | Retry (optional) |

---

# 🔐 2. LOGIN SCREEN

## States

* Idle
* Typing
* Validating
* Loading
* Success
* Error

## What user sees

* Inputs (phone, password)
* Login button
* OTP option
* Error messages (inline)

## Actions

* Login
* Login with OTP
* Go to Register
* Forgot Password

---

## Failure Table

| Scenario          | Message                     | Action           |
| ----------------- | --------------------------- | ---------------- |
| Wrong credentials | "Invalid phone or password" | Retry            |
| Network error     | "Check your connection"     | Retry            |
| Empty fields      | "Fill all fields"           | Highlight inputs |

---

## Action Rules

| State       | Button             |
| ----------- | ------------------ |
| Idle        | Login (disabled)   |
| Valid input | Login (enabled)    |
| Loading     | Spinner (disabled) |
| Error       | Retry enabled      |

---

# 🏠 3. CUSTOMER HOME SCREEN

## States

* Loading (fetch A/B/C engines)
* Loaded
* Empty (no nearby data)
* Error
* Refreshing

## What user sees

* Feed (products/services/events) 
* Location
* Categories
* Sections (Near you, Services, Events)

## Actions

* Search
* Tap category
* Tap product/service/event
* Change location
* Pull to refresh

---

## Failure Table

| Scenario       | Message                              | Action          |
| -------------- | ------------------------------------ | --------------- |
| No data nearby | "Nothing near you yet"               | Change location |
| Location off   | "Enable location for better results" | Open settings   |
| Network error  | "Failed to load content"             | Retry           |

---

## Action Rules

| State   | Button               |
| ------- | -------------------- |
| Loading | Skeleton UI          |
| Loaded  | All actions enabled  |
| Empty   | CTA: Change location |
| Error   | Retry                |

---

# 📦 4. PRODUCT DETAIL SCREEN

## States

* Loading vendors
* Loaded
* No vendors
* Error

## What user sees

* Product info
* Vendor list 
* Price range
* CTA buttons

## Actions

* Select vendor
* View all vendors
* Request item
* Go to nearest shop

---

## Failure Table

| Scenario      | Message                       | Action       |
| ------------- | ----------------------------- | ------------ |
| No vendors    | "No vendors available nearby" | Request item |
| Network error | "Unable to load vendors"      | Retry        |

---

## Action Rules

| State      | Button           |
| ---------- | ---------------- |
| Loading    | Disabled         |
| Loaded     | All CTAs active  |
| No vendors | Request CTA only |
| Error      | Retry            |

---

# 🏪 5. VENDOR SELECTION SCREEN

## States

* Loading
* Loaded
* Vendor selected
* Error

## What user sees

* Vendor list
* Filters
* Map (optional)

## Actions

* Select vendor
* Apply filters
* Continue

---

## Failure Table

| Scenario                 | Message                  | Action        |
| ------------------------ | ------------------------ | ------------- |
| No vendors match filters | "No results"             | Reset filters |
| Network error            | "Failed to load vendors" | Retry         |

---

## Action Rules

| State           | Button              |
| --------------- | ------------------- |
| No selection    | Continue (disabled) |
| Vendor selected | Continue (enabled)  |
| Loading         | Disabled            |

---

# 💳 6. PAYMENT FLOW SCREEN (CRITICAL)

## States

* Draft (TRX not created)
* Validating
* Processing
* Success
* Failure

## What user sees

* Summary
* Cost breakdown
* Payment method 

## Actions

* Change fulfillment
* Select payment
* Confirm

---

## Failure Table

| Scenario           | Message                      | Action           |
| ------------------ | ---------------------------- | ---------------- |
| Payment failed     | "Payment unsuccessful"       | Retry            |
| Vendor unavailable | "Vendor no longer available" | Re-select vendor |
| Price changed      | "Price updated"              | Accept new price |
| Network error      | "Connection issue"           | Retry            |

---

## Action Rules

| State      | Button             |
| ---------- | ------------------ |
| Draft      | Confirm enabled    |
| Processing | Disabled + spinner |
| Failure    | Retry              |
| Success    | Redirect           |

---

# 📦 7. ORDER LIST SCREEN

## States

* Loading
* Loaded
* Empty
* Error

## What user sees

* Orders grouped (Active / Completed) 

## Actions

* View order
* Track order
* Filter

---

## Failure Table

| Scenario      | Message                 | Action     |
| ------------- | ----------------------- | ---------- |
| No orders     | "No orders yet"         | Go to Home |
| Network error | "Failed to load orders" | Retry      |

---

## Action Rules

| State  | Button      |
| ------ | ----------- |
| Empty  | CTA: Browse |
| Loaded | All enabled |
| Error  | Retry       |

---

# 📍 8. ORDER TRACKING SCREEN

## States

* Preparing
* Assigned to rider
* In transit
* Arriving
* Completed
* Error

## What user sees

* Map
* Status updates
* Rider info 

## Actions

* Call rider
* Chat
* Refresh

---

## Failure Table

| Scenario           | Message                            | Action          |
| ------------------ | ---------------------------------- | --------------- |
| GPS lost           | "Tracking temporarily unavailable" | Retry           |
| Rider unresponsive | "Trying to reconnect"              | Contact support |

---

## Action Rules

| State           | Button                  |
| --------------- | ----------------------- |
| Active delivery | Contact buttons enabled |
| Completed       | Disabled                |
| Error           | Retry                   |

---

# 🛵 9. RIDER JOB FEED

## States

* Offline
* Loading
* Jobs available
* No jobs
* Error

## What user sees

* Job cards 

## Actions

* View job
* Filter jobs

---

## Failure Table

| Scenario      | Message                | Action      |
| ------------- | ---------------------- | ----------- |
| No jobs       | "No jobs available"    | Stay online |
| Network error | "Failed to fetch jobs" | Retry       |

---

## Action Rules

| State          | Button   |
| -------------- | -------- |
| Offline        | Disabled |
| Jobs available | Enabled  |
| No jobs        | Passive  |
| Error          | Retry    |

---

# 🏪 10. VENDOR REQUEST INBOX

## States

* Loading
* Requests available
* No requests
* Error

## What user sees

* Request cards 

## Actions

* Accept
* Reject
* View details

---

## Failure Table

| Scenario      | Message                   | Action |
| ------------- | ------------------------- | ------ |
| No requests   | "No incoming requests"    | Wait   |
| Network error | "Failed to load requests" | Retry  |

---

## Action Rules

| State     | Button                |
| --------- | --------------------- |
| Available | Accept/Reject enabled |
| Loading   | Disabled              |
| Error     | Retry                 |

---
* No dead ends
* Always show next action
* Real-time feedback everywhere
* Every screen tied to **TRX state**

---

