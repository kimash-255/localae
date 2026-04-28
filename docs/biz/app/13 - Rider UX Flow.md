# Rider UX Flow

This document focuses on how riders receive jobs, execute deliveries, and track earnings.

## 1. Rider Goal

| Goal | Meaning |
| --- | --- |
| Become available easily | Signal readiness to receive work |
| Understand jobs quickly | Know whether to accept a delivery |
| Deliver efficiently | Navigate and complete with minimal confusion |
| See earnings clearly | Understand how completed work translates into money |

## 2. Rider Primary Journeys

| Journey | Start | End |
| --- | --- | --- |
| Availability setup | Rider Home | Rider is online for jobs |
| Job acceptance | Job Feed | Rider is assigned |
| Delivery execution | Live Navigation | Delivery completed |
| Earnings review | Earnings Overview | Rider understands income and withdrawals |

## 3. Rider Delivery UX Flow

| Order | Screen | Rider Intent | Needed Output |
| --- | --- | --- | --- |
| 1 | Rider Home Screen | See readiness state | Rider context |
| 2 | Availability Toggle Screen | Go online | Active status |
| 3 | Job Feed Screen | Browse jobs | Candidate jobs |
| 4 | Job Detail Screen | Evaluate job | Accept decision |
| 5 | Accept / Reject Screen | Commit to job | Assignment confirmed |
| 6 | Live Navigation Screen | Execute route | Delivery in motion |
| 7 | Delivery Tracking Screen | Follow progress milestones | Status visibility |
| 8 | Completion Screen | Finish job | Delivery completed |
| 9 | Earnings Overview / Withdrawals / History | Review money | Settlement visibility |

## 4. Rider Use Cases

| Use Case | Description | Main Screens |
| --- | --- | --- |
| Go online for work | Rider wants to start receiving jobs | Rider Home, Availability Toggle |
| Decide whether a job is worth it | Rider needs enough context to accept or reject | Job Feed, Job Detail |
| Complete a pickup and drop-off | Rider needs accurate route and state updates | Navigation, Tracking, Completion |
| Confirm proof of completion | Rider wants closure and fewer disputes | Completion |
| Review earnings | Rider wants visibility into value earned | Earnings Overview, History |

## 5. Data Needed For Rider UX

| Screen / Module | Data Needed |
| --- | --- |
| Rider Home | Availability status, job readiness state, quick metrics |
| Job Feed | Job ID, pickup area, drop-off area, distance, estimated payout, urgency |
| Job Detail | Full route info, package or order summary, merchant info, customer info, payout breakdown |
| Accept / Reject | Acceptance timer, assignment state, failure reason if unavailable |
| Live Navigation | Route geometry, pickup point, drop-off point, live location, ETA |
| Delivery Tracking | Milestone statuses, proof states, communication links |
| Completion | Delivery confirmation, notes, proof-of-delivery metadata |
| Earnings Overview / History | Balance, completed jobs, payout history, withdrawal status |

## 6. Rider Decision Information

| Decision | Information Needed |
| --- | --- |
| Should I take this job? | Distance, time, payout, pickup complexity, urgency |
| Am I still on track? | ETA, route progress, pickup or drop-off state |
| Was this completed correctly? | Delivery confirmation, proof, status update |
| How much did I earn? | Gross payout, fees if any, withdrawal availability |

## 7. Rider UX Rules

| Rule | Meaning |
| --- | --- |
| Job cards must be scannable | Riders need to decide fast |
| Navigation must reduce stress | Core delivery data should be visible at a glance |
| Completion must be explicit | Delivery closure should be clear to prevent disputes |
| Earnings should feel immediate | Riders should quickly understand the financial result of work |
