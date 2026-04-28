# Screen Build Order

This is the recommended implementation order for building the app screens from the very first entry screen to the last shared utility screen.

| Build # | Screen | App Area | Why It Comes Here |
| --- | --- | --- | --- |
| 1 | Splash Screen | Core / Entry | App boot, token check, and route handoff start here. |
| 2 | Login Screen | Auth | First usable auth entry after splash. |
| 3 | Register Screen | Auth | Completes the base auth flow. |
| 4 | Role Selection Screen | Auth / Routing | Required fallback before sending users into the right app shell. |
| 5 | Customer Home Screen | Customer | Main post-login landing screen and discovery hub. |
| 6 | Search Results Screen | Customer | Extends discovery after Home and search input. |
| 7 | Product Detail Screen | Customer | Core commerce detail view after discovery. |
| 8 | Service Detail Screen | Customer | Service-side equivalent of product detail. |
| 9 | Vendor Map / Nearby Sellers Screen | Customer | Needed once product discovery can route to supply. |
| 10 | Vendor Selection Screen | Customer | Lets users choose where and how to fulfill an order. |
| 11 | Payment Flow Screen | Global / Commerce | Critical transaction screen after vendor selection. |
| 12 | Order List Screen | Customer | First order-management view after checkout starts working. |
| 13 | Order Detail Screen | Customer | Required to inspect a single order. |
| 14 | Order Tracking Screen | Customer | Completes the customer order lifecycle. |
| 15 | Wallet Home Screen | Customer | Starts the payment and transaction area after orders exist. |
| 16 | Transaction History Screen | Customer | Follows wallet home for payment visibility. |
| 17 | Payment Methods Screen | Customer | Finishes wallet setup and saved payment management. |
| 18 | Profile Screen | Customer | Core account screen after commerce flow is stable. |
| 19 | Notifications Screen | Shared / Customer | Useful once orders and payments can generate alerts. |
| 20 | Settings Screen | Shared / Customer | Basic account and app preferences after profile. |
| 21 | Vendor Dashboard Screen | Vendor | First vendor landing screen and operational overview. |
| 22 | Analytics Screen | Vendor | Extends dashboard insights once the vendor shell exists. |
| 23 | Inventory List Screen | Vendor | Base inventory management view. |
| 24 | Add Product Screen | Vendor | Product creation depends on inventory flow existing first. |
| 25 | Add Service Screen | Vendor | Service creation follows the same inventory pattern. |
| 26 | Edit Item Screen | Vendor | Comes after add flows so editing reuses existing forms. |
| 27 | Request Inbox Screen | Vendor | Starts vendor-side order handling. |
| 28 | Order Detail Screen (Vendor View) | Vendor | Needed to inspect incoming requests. |
| 29 | Fulfillment Center Screen | Vendor | Completes vendor processing and fulfillment flow. |
| 30 | Event List Screen | Vendor / Events | Event module starts after core selling flow is stable. |
| 31 | Event Detail Screen | Vendor / Events | Detail layer for selected events. |
| 32 | Participation Screen | Vendor / Events | Lets vendors join and manage event participation. |
| 33 | Vendor Profile Screen | Vendor | Public/vendor account presence after operations screens. |
| 34 | Ratings Screen | Vendor | Depends on profile and transaction activity. |
| 35 | Settings Screen (Vendor) | Vendor | Final vendor account configuration layer. |
| 36 | Rider Home Screen | Rider | First rider landing screen and availability context. |
| 37 | Availability Toggle Screen | Rider | Needed before job acceptance flow. |
| 38 | Job Feed Screen | Rider | Core rider work queue. |
| 39 | Job Detail Screen | Rider | Detail layer for selected jobs. |
| 40 | Accept / Reject Screen | Rider | Action step after job detail. |
| 41 | Live Navigation Screen | Rider | Starts the real-time delivery flow. |
| 42 | Delivery Tracking Screen | Rider | Mid-delivery progress screen. |
| 43 | Completion Screen | Rider | Ends the delivery lifecycle. |
| 44 | Earnings Overview Screen | Rider | Makes sense after jobs can be completed. |
| 45 | Withdrawals Screen | Rider | Depends on rider earnings flow. |
| 46 | Earnings History Screen | Rider | Final financial record view for riders. |
| 47 | Rider Profile Screen | Rider | Rider account screen after core work flow is stable. |
| 48 | Settings Screen (Rider) | Rider | Final rider preferences screen. |
| 49 | Wallet Modal Screen | Global | Shared wallet overlay after customer, vendor, and rider money flows exist. |
| 50 | Support Screen | Global | Shared support layer after the main flows are usable. |
| 51 | Settings Screen (Global) | Global | Final cross-app settings surface. |

## Notes

| Topic | Guidance |
| --- | --- |
| Best MVP cutoff | Stop at Build #14 if you want the first complete customer commerce loop. |
| Best phase 2 cutoff | Stop at Build #29 if you want customer + vendor order fulfillment working. |
| Best phase 3 cutoff | Finish through Build #48 for full rider operations. |
| Final polish layer | Builds #49-#51 are shared system utilities and should come after the core role-based flows are stable. |
