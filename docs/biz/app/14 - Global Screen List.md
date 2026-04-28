# Global Screen List

This document lists the screens and system modules that belong to the global app flow.

## 1. Global Screen Inventory

| # | Screen / Module | Type | Primary Purpose | Entry Trigger | Next Step |
| --- | --- | --- | --- | --- | --- |
| G1 | Splash Screen | Screen | Boot app and check session state | App launch | Login or Role Router |
| G2 | Login Screen | Screen | Authenticate existing user | No valid session | Role Router |
| G3 | Register Screen | Screen | Create a new account and persist user type | New user entry | Role Router |
| G4 | Role Router | Logic Module | Route user into correct app shell using stored user type | Auth success or splash validation | Customer, Vendor, or Rider app |
| G5 | App Shell Loader | Logic Module | Load role-specific root navigation and required boot data | Role resolved | Role-based home screen |
| G6 | Global Transaction State | Logic Module | Keep transaction status consistent across roles | Transaction creation | Orders, fulfillment, or delivery flow |
| G7 | Global Deep Link Resolver | Logic Module | Route app opens from notifications, links, or support contexts | External link or notification tap | Target screen |

## 2. Global Flow Ownership

| Screen / Module | Owned By |
| --- | --- |
| Splash Screen | `features/auth` |
| Login Screen | `features/auth` |
| Register Screen | `features/auth` |
| Role Router | `features/auth` or `app` routing layer |
| App Shell Loader | `app` routing layer |
| Global Transaction State | shared transaction orchestration layer |
| Global Deep Link Resolver | shared navigation layer |

## 3. Global Screen Data Needs

| Screen / Module | Key Data Needed |
| --- | --- |
| Splash Screen | token, refresh token, cached role, app config |
| Login Screen | credentials, validation state, auth errors |
| Register Screen | name, phone or email, password or OTP, validation rules |
| Role Router | user role, account state, feature access |
| App Shell Loader | bootstrapped role data, navigation readiness |
| Global Transaction State | transaction ID, actor IDs, status, timestamps |
| Global Deep Link Resolver | target route, payload, permission state |

## 4. Global Screen Notes

| Rule | Meaning |
| --- | --- |
| Global screens should stay lean | They should route or coordinate, not carry heavy business UI |
| Authentication should be isolated | Auth concerns should not leak into customer, vendor, or rider features |
| Routing must be deterministic | The same user state should always lead to the same shell |
