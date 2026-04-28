# Shared UX Flow

This document covers UX modules that are reused across customer, vendor, and rider flows.

## 1. Scope

| Shared Module | Purpose |
| --- | --- |
| Notifications | Inform users about changes, actions, and reminders |
| Wallet | Show payments, earnings, balances, and history |
| Support | Help users resolve issues |
| Profile | Show identity, trust signals, and account activity |
| Settings | Preferences, security, and account controls |
| Ratings / Reviews | Build trust after real transactions |

## 2. Why Shared UX Matters

| Reason | Meaning |
| --- | --- |
| Consistency | Users should not relearn the same system in each role area |
| Reuse | Shared modules reduce duplicated implementation |
| Trust | Wallet, notifications, and profile make the platform feel reliable |
| Recovery | Support and settings provide escape hatches when flows break |

## 3. Shared Module Use Cases

| Use Case | User Type | Module | Outcome |
| --- | --- | --- | --- |
| Check order or job alerts | All users | Notifications | User knows what changed |
| View payment history | Customer, vendor, rider | Wallet | User sees financial status |
| Withdraw earnings | Vendor, rider | Wallet | Payout action starts |
| Update personal details | All users | Profile / Settings | Account remains current |
| Contact support | All users | Support | Issue can be resolved |
| Review trust indicators | Customer, vendor, rider | Profile / Ratings | Better confidence in transactions |

## 4. Shared UX Flow By Module

### 4.1 Notifications

| Step | User Action | System Response |
| --- | --- | --- |
| 1 | User opens notifications | Load recent notification feed |
| 2 | User taps a notification | Deep link to relevant screen |
| 3 | User marks read or clears | Update unread state |

### 4.2 Wallet

| Step | User Action | System Response |
| --- | --- | --- |
| 1 | User opens wallet | Load balance and summary |
| 2 | User views history | Load transaction list |
| 3 | User adds payment method or withdraws | Start payment or payout subflow |
| 4 | User sees completion | Update status and ledger summary |

### 4.3 Support

| Step | User Action | System Response |
| --- | --- | --- |
| 1 | User opens support | Show help categories and contact options |
| 2 | User chooses an issue | Load issue-specific help path |
| 3 | User submits report | Create support case or handoff |

### 4.4 Profile

| Step | User Action | System Response |
| --- | --- | --- |
| 1 | User opens profile | Load identity, verification, activity summary |
| 2 | User edits details | Validate and save changes |
| 3 | User reviews trust data | Show ratings, badges, and activity history |

### 4.5 Settings

| Step | User Action | System Response |
| --- | --- | --- |
| 1 | User opens settings | Show account and preference options |
| 2 | User changes preferences | Save updates |
| 3 | User performs account action | Confirm, then execute |

## 5. Shared Screen Inventory

| Module | Possible Screens |
| --- | --- |
| Notifications | Notifications Screen |
| Wallet | Wallet Home, Transaction History, Payment Methods, Wallet Modal |
| Support | Support Screen |
| Profile | Profile Screen, Vendor Profile Screen, Rider Profile Screen |
| Settings | Customer Settings, Vendor Settings, Rider Settings, Global Settings |
| Ratings | Ratings Screen |

## 6. Data Needed For Shared UX

| Module | Data Needed |
| --- | --- |
| Notifications | Notification ID, type, title, body, read state, target screen, created time |
| Wallet | Balance, transaction list, payment methods, payout methods, ledger summary |
| Support | Issue category, ticket status, user contact details, transaction reference |
| Profile | Name, avatar, phone, role, verification status, ratings summary, activity summary |
| Settings | Notification preferences, privacy choices, account security state, app preferences |
| Ratings | Rating value, reviewer, review target, transaction reference, timestamp |

## 7. Key UX States

| Module | Important States |
| --- | --- |
| Notifications | Empty, unread, read, loading, error |
| Wallet | Loading, funded, empty, pending, failed, withdrawn |
| Support | Browse, submit, waiting, resolved |
| Profile | Viewing, editing, saving, error |
| Settings | Idle, updating, success, error |

## 8. Shared UX Rules

| Rule | Meaning |
| --- | --- |
| Deep links should work | Shared modules should always return users to the right context |
| Financial data must be clear | Wallet balances and transaction states cannot be ambiguous |
| Support must reference real context | If a user has an issue, support should know the related transaction or screen |
| Settings should be safe | Sensitive actions need confirmation |
| Shared does not mean generic business logic | Shared modules should support all roles without owning role-specific workflows |
