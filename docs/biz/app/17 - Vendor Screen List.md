# Vendor Screen List

This document lists vendor-facing screens for operations, inventory, fulfillment, events, and business trust.

## 1. Vendor Screen Inventory

| # | Screen | Flow Area | Primary Purpose | Main Outcome |
| --- | --- | --- | --- | --- |
| V1 | Vendor Dashboard Screen | Operations | Show business overview and incoming demand | Vendor knows what needs attention |
| V2 | Analytics Screen | Operations | Show performance and business insight | Vendor understands trends |
| V3 | Inventory List Screen | Inventory | Show current products and services | Vendor sees all active supply |
| V4 | Add Product Screen | Inventory | Create a new product listing | Product added |
| V5 | Add Service Screen | Inventory | Create a new service listing | Service added |
| V6 | Edit Item Screen | Inventory | Update an existing listing | Listing improved |
| V7 | Request Inbox Screen | Fulfillment | Show incoming requests and orders | Vendor triages demand |
| V8 | Order Detail Screen (Vendor View) | Fulfillment | Show request details clearly | Vendor can decide next action |
| V9 | Fulfillment Center Screen | Fulfillment | Manage prep, handoff, completion | Work is executed |
| V10 | Event List Screen | Events | Show available event opportunities | Vendor evaluates events |
| V11 | Event Detail Screen | Events | Show event details and participation value | Vendor decides to join |
| V12 | Participation Screen | Events | Manage event presence and participation | Event presence active |
| V13 | Vendor Profile Screen | Trust | Show vendor identity and business presence | Vendor profile visible |
| V14 | Ratings Screen | Trust | Show feedback and reputation | Vendor understands trust state |

## 2. Vendor Flow Grouping

| Group | Screens |
| --- | --- |
| Operations | V1, V2 |
| Inventory | V3, V4, V5, V6 |
| Fulfillment | V7, V8, V9 |
| Events | V10, V11, V12 |
| Trust | V13, V14 |

## 3. Vendor Screen Data Needs

| Screen | Key Data Needed |
| --- | --- |
| Vendor Dashboard Screen | open requests, pending tasks, sales summary, alerts |
| Analytics Screen | earnings, conversions, order volume, repeat activity |
| Inventory List Screen | listings, categories, stock or availability, visibility state |
| Add Product Screen | product fields, categories, price rules, images |
| Add Service Screen | service fields, service modes, price rules, availability |
| Edit Item Screen | existing item data, editable fields, publish status |
| Request Inbox Screen | request ID, customer summary, request type, urgency, timestamps |
| Order Detail Screen (Vendor View) | line items, notes, customer details, fulfillment method, rider handoff state |
| Fulfillment Center Screen | prep state, pickup readiness, rider assignment, completion state |
| Event List Screen | event summaries, dates, fees, opportunity score |
| Event Detail Screen | event rules, demand estimate, participation requirements |
| Participation Screen | chosen offerings, participation status, event setup details |
| Vendor Profile Screen | identity, verification, store info, ratings summary |
| Ratings Screen | reviews, scores, linked transactions, trends |

## 4. Vendor Screen Notes

| Rule | Meaning |
| --- | --- |
| Inbox and fulfillment are the operational core | They should stay fast and practical |
| Inventory screens should share a data model | Product and service creation should feel consistent |
| Event screens should stay optional | They support growth but should not clutter core order work |
