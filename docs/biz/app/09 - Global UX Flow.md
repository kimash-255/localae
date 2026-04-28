# Global UX Flow

This document covers the app-wide UX that exists before role-specific flows begin and the platform-wide logic that coordinates customer, vendor, and rider journeys.

## 1. Scope

| Area | Included |
| --- | --- |
| App boot | Splash, session check, config load |
| Authentication entry | Login, register, account handoff |
| Role routing | Role detection, role assignment, role-based redirection |
| Cross-role transaction orchestration | Customer creates demand, vendor executes, rider delivers |
| Global state continuity | Notifications, status changes, settlement visibility |

## 2. Main Actors

| Actor | Responsibility in Global Flow |
| --- | --- |
| Customer | Creates demand by browsing, requesting, or ordering |
| Vendor / Provider | Accepts and fulfills supply-side work |
| Rider | Executes delivery or transport where needed |
| Platform | Routes demand, records transactions, tracks status, splits value |

## 3. Global Journey Overview

| Step | Flow Stage | Trigger | Output |
| --- | --- | --- | --- |
| 1 | App boot | User opens app | App state begins loading |
| 2 | Session check | Splash completes checks | Valid session or auth required |
| 3 | Auth entry | No valid session or new user | Authenticated account |
| 4 | Role routing | User identity is known | Customer, vendor, or rider shell selected |
| 5 | Demand capture | Customer starts an action | Intent to buy, book, or participate |
| 6 | Supply routing | Platform locates vendor/provider | Available supply identified |
| 7 | Transaction creation | User confirms action | Transaction record created |
| 8 | Execution | Vendor and rider act | Order or service progresses |
| 9 | Visibility | Updates happen | All actors see relevant status |
| 10 | Settlement | Work is completed | Balances and outcomes recorded |

## 4. Global Entry Flow

| Order | Screen / Module | Purpose | Success Path | Failure Path |
| --- | --- | --- | --- | --- |
| 1 | Splash Screen | Load app, check session, fetch role | Go to Role Router | Retry or go to Login |
| 2 | Login Screen | Authenticate existing user | Go to Role Router | Show auth error |
| 3 | Register Screen | Create account and save user type | Go to Role Router | Show validation error |
| 4 | Role Router | Send user to correct root area using stored user type | Open customer, vendor, or rider app | Return to auth / role recovery |

## 5. End-To-End Cross-Role UX Flow

| Step | Customer Action | Vendor Action | Rider Action | Platform Action |
| --- | --- | --- | --- | --- |
| 1 | Opens app | - | - | Boots, checks state |
| 2 | Browses or searches | - | - | Surfaces relevant content |
| 3 | Chooses product, service, or event path | Sees possible incoming demand | - | Matches demand to supply |
| 4 | Confirms order or request | Receives request | - | Creates transaction |
| 5 | Watches progress | Accepts and starts work | Receives job if delivery is needed | Updates statuses |
| 6 | Tracks fulfillment | Prepares or completes work | Navigates and delivers | Coordinates execution |
| 7 | Sees completion | Receives outcome and earnings | Receives outcome and earnings | Splits and settles value |

## 6. Core Use Cases

| Use Case | Primary User | Description | Key Screens |
| --- | --- | --- | --- |
| Sign in and resume | All users | User returns and continues where they left off | Splash, Login, Role Router |
| First-time onboarding | All users | User creates account and gets a user type during registration | Register, Role Router |
| Start an order | Customer | User discovers an item and initiates purchase | Home, Search, Detail, Payment |
| Fulfill an order | Vendor | Vendor accepts and processes demand | Dashboard, Inbox, Detail, Fulfillment |
| Deliver an order | Rider | Rider accepts a job and completes route | Job Feed, Navigation, Completion |
| Resolve friction | All users | User reviews support, notifications, or settings | Notifications, Support, Settings |

## 7. Global UX Rules

| Rule | Meaning |
| --- | --- |
| One clear next step | Every screen should lead naturally into the next action |
| Role-aware routing | Users should only see the app shell that matches their role |
| Status continuity | Every transaction should have a visible state |
| Transaction first | The system must always preserve a transaction record |
| Fail gracefully | Errors should never break the ability to recover or retry |

## 8. Data Needed For Global UX

| Data Group | Needed For |
| --- | --- |
| Session token | Auth validation and auto-login |
| User profile | Identity, role, verification, settings |
| Role value | Routing to customer, vendor, or rider shell |
| App config | Feature flags, environment, version gates |
| Transaction IDs | Cross-role traceability |
| Notification payloads | Alerts and state updates |
| Wallet / ledger summary | Settlement visibility |

## 9. Screen-Level Data Requirements

| Screen / Module | Data Needed |
| --- | --- |
| Splash Screen | Token, refresh token, app config, cached role |
| Login Screen | Phone or email credential fields, auth status, error state |
| Register Screen | Identity inputs, password or OTP flow, validation rules |
| Role Router | User role, account status, permission state |

## 10. Outputs This Flow Must Produce

| Output | Why It Matters |
| --- | --- |
| Authenticated user session | Enables all downstream flows |
| Correct role assignment | Keeps navigation clean |
| Platform transaction record | Anchors money, fulfillment, and status flows |
| Shared status model | Lets every actor understand current progress |
| Recovery path on failure | Prevents dead ends in the journey |
