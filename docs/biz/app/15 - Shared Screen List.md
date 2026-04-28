# Shared Screen List

This document lists screens and modules that are reused across roles.

## 1. Shared Screen Inventory

| # | Screen / Module | Type | Used By | Primary Purpose |
| --- | --- | --- | --- | --- |
| S1 | Notifications Screen | Screen | All users | Show alerts, updates, and deep links |
| S2 | Wallet Home Screen | Screen | Customer, Vendor, Rider | Show balances and money summary |
| S3 | Transaction History Screen | Screen | Customer, Vendor, Rider | Show past money movements |
| S4 | Payment Methods Screen | Screen | Mostly Customer, later all roles as needed | Manage payment instruments |
| S5 | Wallet Modal Screen | Modal | All users where relevant | Quick wallet access from anywhere |
| S6 | Support Screen | Screen | All users | Help users resolve issues |
| S7 | Profile Screen | Screen | Customer | Show customer identity and activity |
| S8 | Vendor Profile Screen | Screen | Vendor | Show vendor identity and trust data |
| S9 | Rider Profile Screen | Screen | Rider | Show rider identity and work summary |
| S10 | Ratings Screen | Screen | Vendor, Rider | Show reputation signals |
| S11 | Settings Screen | Screen | Customer | Account and preference controls |
| S12 | Settings Screen (Vendor) | Screen | Vendor | Vendor-specific settings |
| S13 | Settings Screen (Rider) | Screen | Rider | Rider-specific settings |
| S14 | Settings Screen (Global) | Screen | All users | Cross-app settings and platform controls |

## 2. Shared Module Inventory

| # | Module | Purpose |
| --- | --- | --- |
| SM1 | Notification Center | Feed state, unread counts, routing targets |
| SM2 | Wallet / Ledger Summary | Unified money status across roles |
| SM3 | Support Case Handler | Case creation and issue tracking |
| SM4 | Identity Summary | Shared profile presentation and trust signals |
| SM5 | Preferences Manager | Notification, privacy, and app settings |

## 3. Shared Screen Data Needs

| Screen / Module | Key Data Needed |
| --- | --- |
| Notifications Screen | notification ID, type, title, message, unread state, target screen |
| Wallet Home Screen | balance, pending amounts, earnings, debts, summary cards |
| Transaction History Screen | transaction list, type, amount, counterparties, timestamps |
| Payment Methods Screen | saved methods, default method, verification state |
| Wallet Modal Screen | quick balance summary, recent transactions, action shortcuts |
| Support Screen | issue category, transaction reference, contact channel, status |
| Profile Screens | user identity, avatar, verification, activity metrics, trust badges |
| Ratings Screen | rating summary, review items, transaction-linked feedback |
| Settings Screens | preferences, security state, connected methods, privacy options |

## 4. Shared Screen Rules

| Rule | Meaning |
| --- | --- |
| Shared does not mean generic clutter | Only truly reusable screens belong here |
| Shared screens should accept context | They should know which user role and transaction context opened them |
| Money screens must stay consistent | Wallet and transaction terminology should be the same across roles |
