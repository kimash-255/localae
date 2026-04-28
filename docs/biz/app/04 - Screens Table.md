
---

# 📊 GLOBAL APP SCREEN STRUCTURE 

## 🌐 Core System Screens (Shared Infrastructure)

| #   | Screen / Feature             | Description                     | Customer | Vendor | Rider |
| --- | ---------------------------- | ------------------------------- | -------- | ------ | ----- |
| 0.1 | Splash Screen                | App initialization/loading      | ✅        | ✅      | ✅     |
| 0.2 | Role Selection / Auth Router | Auto-detect or select user role | ✅        | ✅      | ✅     |
| 3   | Notifications                | System + transactional alerts   | ✅        | ✅      | ✅     |
| 4   | Wallet & Payments            | Transactions, earnings, payouts | ✅        | ✅      | ✅     |
| 5   | Settings                     | App configuration & preferences | ✅        | ✅      | ✅     |

---

## 🧍 CUSTOMER APP FLOWS

### 🛒 Product Commerce Flow

| #  | Screen                      | Purpose                         |
| -- | --------------------------- | ------------------------------- |
| 1  | Home / Explore              | Main discovery hub              |
| 2  | Search Results              | Filtered product/service search |
| 3A | Product Detail              | Product information view        |
| 4A | Vendor Map / Nearby Sellers | Locate sellers                  |
| 5A | Vendor Selection            | Choose vendor & delivery option |
| 6A | Order Tracking              | Track order lifecycle           |

---

### 🛠 Service Booking Flow

| #  | Screen                 | Purpose             |
| -- | ---------------------- | ------------------- |
| 3B | Service Detail         | Service overview    |
| 4B | Provider List          | Available providers |
| 5B | Service Mode Selection | Choose service type |
| 6B | Service Request        | Submit booking      |
| 7B | Service Status         | Track progress      |

---

### 🎟 Events Flow

| #  | Screen               | Purpose                    |
| -- | -------------------- | -------------------------- |
| 3C | Events Feed          | Browse events              |
| 4C | Event Detail         | Event information hub      |
| 5C | Participation Screen | Join / interact / purchase |
| 6C | Event Marketplace    | Live vendors at event      |
| 7C | Event Tracking       | Orders + attendance status |

---

## 🏪 VENDOR / PROVIDER APP FLOWS

| # | Screen                     | Purpose                         |
| - | -------------------------- | ------------------------------- |
| 1 | Vendor Dashboard           | Overview + incoming requests    |
| 2 | Inventory / Services Setup | Manage listings                 |
| 3 | Request Inbox              | Accept / reject orders          |
| 4 | Order / Service Detail     | View request details            |
| 5 | Fulfillment Center         | Process delivery/service        |
| 6 | Event Participation        | Join/manage events              |
| 7 | Vendor Profile             | Ratings, analytics, performance |

---

## 🛵 RIDER APP FLOWS

| # | Screen          | Purpose                       |
| - | --------------- | ----------------------------- |
| 1 | Rider Home      | Availability + job feed       |
| 2 | Job Feed        | Available deliveries/rides    |
| 3 | Job Detail      | Accept/decline job            |
| 4 | Navigation      | Live trip tracking            |
| 5 | Completion      | Delivery complete + rating    |
| 6 | Earnings Wallet | Withdrawals + income tracking |

---

## 🔥 SYSTEM-WIDE SHARED MODULES

| Screen               | Purpose                  |
| -------------------- | ------------------------ |
| Splash Screen        | App boot                 |
| Auth / Role Router   | Identity + routing logic |
| Notifications Center | Unified alerts system    |
| Wallet System        | Payments + earnings      |
| Settings             | Global configuration     |

---
