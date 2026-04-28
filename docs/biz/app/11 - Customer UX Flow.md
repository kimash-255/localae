# Customer UX Flow

This document focuses on the customer journey from discovery to post-purchase confidence.

## 1. Customer Goal

| Goal | Meaning |
| --- | --- |
| Discover quickly | Find products, services, and events without friction |
| Decide confidently | Understand availability, price, trust, and fulfillment options |
| Complete action fast | Order, book, or join with minimal steps |
| Track progress clearly | Always know what is happening after commitment |

## 2. Customer Primary Journeys

| Journey | Start | End |
| --- | --- | --- |
| Product commerce | Home / Search | Order delivered or picked up |
| Service booking | Home / Search | Service completed |
| Event participation | Home / Events | Event participation or event-linked order completed |
| Post-purchase management | Orders / Wallet / Notifications | User is informed and ready to return |

## 3. Customer Product UX Flow

| Order | ID | Screen | User Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | C1 | Home / Explore | Browse nearby options | Discovery entry |
| 2 | C2 | Search Results | Narrow options | Relevant shortlist |
| 3 | C3 | Product Detail | Evaluate item | Purchase intent |
| 4 | C7 | Vendor Map / Nearby Sellers | Compare availability | Nearby options |
| 5 | C8 | Vendor Selection | Choose where to buy | Fulfillment decision |
| 6 | C11 | Payment Flow | Confirm transaction | Order created |
| 7 | C15 / C16 | Order List / Order Detail | Review transaction | Order visibility |
| 8 | C17 | Order Tracking | Follow status | Completion confidence |

## 4. Customer Service UX Flow

| Order | ID | Screen | User Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | C1 | Home / Explore | Discover services | Demand signal |
| 2 | C2 | Search Results | Find a relevant provider | Shortlist |
| 3 | C4 | Service Detail | Understand offering | Booking intent |
| 4 | C9 | Provider List | Compare providers | Provider selected |
| 5 | C10 | Service Mode Selection | Choose how service happens | Mode confirmed |
| 6 | C12 | Service Request | Submit booking | Request created |
| 7 | C18 | Service Status | Watch progress | Service completion |

## 5. Customer Events UX Flow

| Order | ID | Screen | User Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | C1 / C5 | Home / Explore / Events entry | Discover active deals or events | Event interest |
| 2 | C5 | Events Feed | Browse event options | Event shortlist |
| 3 | C6 | Event Detail | Evaluate offer and logistics | Participation intent |
| 4 | C13 | Participation Screen | Join or purchase | Participation record |
| 5 | C14 | Event Marketplace | Buy from event vendors | Event-linked order |
| 6 | C19 | Event Tracking | Monitor status | Event outcome |

## 6. Customer Use Cases

| Use Case | Description | Main Screens |
| --- | --- | --- |
| Find a nearby product | User wants the fastest path from need to local supply | `C1`, `C2`, `C3`, `C8` |
| Book a service | User wants a provider, mode, and timeline | `C2`, `C4`, `C12` |
| Buy from an event | User is driven by urgency or community activity | `C5`, `C6`, `C13` |
| Track an order | User wants certainty after paying | `C15`, `C16`, `C17` |
| Reuse trust signals | User wants confidence in seller choice | `C3`, `C8`, `S7-S10` |

## 7. Data Needed For Customer UX

| ID | Screen / Module | Data Needed |
| --- | --- | --- |
| C1 | Home / Explore | Location, categories, featured items, nearby products, nearby services, events |
| C2 | Search Results | Query, filters, sort, availability, distance, price ranges |
| C3 | Product Detail | Product ID, images, description, price, stock, vendor options, reviews |
| C4 | Service Detail | Service ID, provider summary, pricing, mode options, availability |
| C7 | Vendor Map / Nearby Sellers | Vendor locations, distance, fulfillment options, open state |
| C8 | Vendor Selection | Vendor list, pricing, ETA, pickup or delivery options |
| C11 | Payment Flow | Selected item, vendor, amount, fees, payment method, address or pickup details |
| C15 / C16 / C17 | Order List / Detail / Tracking | Order ID, line items, vendor info, rider info, status timeline |

## 8. Customer Decision Information

| Decision | Information Needed |
| --- | --- |
| Is this worth buying? | Price, quality, availability, trust signals |
| Who should fulfill it? | Distance, delivery option, seller rating, ETA |
| Can I pay safely? | Total cost, fee breakdown, payment method status |
| Can I trust the result? | Order status, notifications, support path |

## 9. Customer UX Rules

| Rule | Meaning |
| --- | --- |
| Discovery must lead to action | Browsing should always have a clear conversion path |
| Details must reduce doubt | Product and service detail screens should answer key buying questions |
| Vendor choice must be comparable | Seller options should be easy to evaluate |
| Post-purchase visibility is mandatory | Tracking and updates are part of the core experience, not extras |
