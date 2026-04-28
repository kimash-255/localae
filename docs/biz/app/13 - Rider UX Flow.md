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

| Order | ID | Screen | Rider Intent | Needed Output |
| --- | --- | --- | --- | --- |
| 1 | R1 | Rider Home Screen | See readiness state | Rider context |
| 2 | R2 | Availability Toggle Screen | Go online | Active status |
| 3 | R3 | Job Feed Screen | Browse jobs | Candidate jobs |
| 4 | R4 | Job Detail Screen | Evaluate job | Accept decision |
| 5 | R5 | Accept / Reject Screen | Commit to job | Assignment confirmed |
| 6 | R6 | Live Navigation Screen | Execute route | Delivery in motion |
| 7 | R7 | Delivery Tracking Screen | Follow progress milestones | Status visibility |
| 8 | R8 | Completion Screen | Finish job | Delivery completed |
| 9 | R9 / R10 / R11 | Earnings Overview / Withdrawals / History | Review money | Settlement visibility |

## 4. Rider Use Cases

| Use Case | Description | Main Screens |
| --- | --- | --- |
| Go online for work | Rider wants to start receiving jobs | `R1`, `R2` |
| Decide whether a job is worth it | Rider needs enough context to accept or reject | `R3`, `R4`, `R5` |
| Complete a pickup and drop-off | Rider needs accurate route and state updates | `R6`, `R7`, `R8` |
| Confirm proof of completion | Rider wants closure and fewer disputes | `R8` |
| Review earnings | Rider wants visibility into value earned | `R9`, `R10`, `R11` |

## 5. Data Needed For Rider UX

| ID | Screen / Module | Data Needed |
| --- | --- | --- |
| R1 | Rider Home | Availability status, job readiness state, quick metrics |
| R3 | Job Feed | Job ID, pickup area, drop-off area, distance, estimated payout, urgency |
| R4 | Job Detail | Full route info, package or order summary, merchant info, customer info, payout breakdown |
| R5 | Accept / Reject | Acceptance timer, assignment state, failure reason if unavailable |
| R6 | Live Navigation | Route geometry, pickup point, drop-off point, live location, ETA |
| R7 | Delivery Tracking | Milestone statuses, proof states, communication links |
| R8 | Completion | Delivery confirmation, notes, proof-of-delivery metadata |
| R9 / R10 / R11 | Earnings Overview / History | Balance, completed jobs, payout history, withdrawal status |

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
