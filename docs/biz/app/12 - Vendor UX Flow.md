# Vendor UX Flow

This document focuses on how vendors manage supply, accept demand, fulfill transactions, and grow trust.

## 1. Vendor Goal

| Goal | Meaning |
| --- | --- |
| Manage supply easily | Keep products and services current |
| Respond to demand fast | Review and act on customer requests |
| Fulfill reliably | Move requests toward completion without confusion |
| Understand business performance | Track earnings, ratings, and activity |

## 2. Vendor Primary Journeys

| Journey | Start | End |
| --- | --- | --- |
| Operations overview | Vendor Dashboard | Vendor understands current state |
| Inventory management | Inventory List | Listings are created or updated |
| Order fulfillment | Request Inbox | Order or service is completed |
| Event participation | Event List | Vendor joins and benefits from event traffic |
| Reputation management | Vendor Profile / Ratings | Stronger trust and performance visibility |

## 3. Vendor Order UX Flow

| Order | ID | Screen | Vendor Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | V1 | Vendor Dashboard | Review business state | Operational awareness |
| 2 | V7 | Request Inbox | Evaluate new demand | Accept or reject |
| 3 | V8 | Order Detail Screen (Vendor View) | Inspect details and requirements | Fulfillment decision |
| 4 | V9 | Fulfillment Center | Prepare, confirm, or hand off work | Work advanced |
| 5 | S1 / S2 / V2 | Wallet / Notifications / Analytics | Review results | Performance loop |

## 4. Vendor Inventory UX Flow

| Order | ID | Screen | Vendor Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | V3 | Inventory List Screen | View all current supply | Listing visibility |
| 2 | V4 | Add Product Screen | Create product listing | Product published |
| 3 | V5 | Add Service Screen | Create service listing | Service published |
| 4 | V6 | Edit Item Screen | Improve or update listing | Listing accuracy |

## 5. Vendor Events UX Flow

| Order | ID | Screen | Vendor Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | V10 | Event List Screen | Find relevant event opportunities | Event shortlist |
| 2 | V11 | Event Detail Screen | Evaluate expected value | Join decision |
| 3 | V12 | Participation Screen | Confirm presence and offerings | Active participation |

## 6. Vendor Use Cases

| Use Case | Description | Main Screens |
| --- | --- | --- |
| Accept a new order | Vendor needs quick triage of incoming demand | `V1`, `V7`, `V8` |
| Prepare an order for rider or pickup | Vendor needs fulfillment controls | `V9` |
| Add a new listing | Vendor wants to expand supply | `V3`, `V4`, `V5` |
| Join a high-traffic event | Vendor wants demand spikes | `V10`, `V12` |
| Review business health | Vendor wants earnings and trust insight | `V2`, `S2`, `S10` |

## 7. Data Needed For Vendor UX

| ID | Screen / Module | Data Needed |
| --- | --- | --- |
| V1 | Vendor Dashboard | Open requests, pending orders, sales summary, alerts |
| V7 | Request Inbox | Request ID, type, customer summary, item summary, timestamps, urgency |
| V8 | Order Detail | Items or service details, price, notes, fulfillment method, address, rider assignment |
| V9 | Fulfillment Center | Preparation state, handoff state, completion state, exceptions |
| V3 | Inventory List | Listing IDs, stock, status, category, visibility |
| V4 / V5 | Add Product / Add Service | Listing fields, pricing rules, images, availability, category metadata |
| V10 / V11 | Event List / Detail | Event date, expected traffic, fees, participation rules, event status |
| V13 / V14 | Vendor Profile / Ratings | Business identity, score summary, review count, verification, activity metrics |

## 8. Vendor Decision Information

| Decision | Information Needed |
| --- | --- |
| Should I accept this request? | Profitability, stock or capacity, timing, distance, workload |
| How should I fulfill it? | Pickup or delivery mode, prep requirements, rider coordination |
| Is this listing healthy? | Visibility, edits needed, stock state, conversion signals |
| Is this event worth joining? | Event size, expected demand, fee structure, timing |

## 9. Vendor UX Rules

| Rule | Meaning |
| --- | --- |
| Inbox must support fast triage | Vendors should quickly know what needs attention |
| Fulfillment must expose operational state | Prep, packed, ready, handed off, completed should be obvious |
| Inventory should be structured | Products and services need consistent data shapes |
| Events should feel optional but high value | Event flow should not clutter core order operations |
