# Development Flow

This document defines the recommended development flow for building the app with a team.

The goal is to make sure everyone knows:

1. what to build first
2. how to pick work
3. where each piece should go
4. how features connect to flows, screens, and architecture
5. how to avoid structure drift while the app grows

## 1. Core Team Rule

| Rule | Meaning |
| --- | --- |
| Build from flow, not from random screens | Every task should trace back to a UX flow and feature |
| Build from features, not from loose files | Screens, hooks, API calls, and types should stay inside the owning feature |
| Keep route files thin | `app/` should mostly expose routes and import feature screens |
| Promote to shared only when truly shared | Do not move code to `shared` too early |

## 2. Development Order

| Phase | Goal | Main Features | Main Screen IDs |
| --- | --- | --- | --- |
| Phase 1 | Entry and customer MVP | `F-G1`, `F-G2`, `F-C1`, `F-C2`, `F-C5`, `F-C6` | `G1-G4`, `C1-C3`, `C7-C8`, `C11`, `C15-C17` |
| Phase 2 | Service and event customer expansion | `F-C3`, `F-C4` | `C4-C6`, `C9-C10`, `C12-C14`, `C18-C19` |
| Phase 3 | Vendor-side execution | `F-V1`, `F-V2`, `F-V3` | `V1-V9` |
| Phase 4 | Rider-side execution | `F-R1`, `F-R2`, `F-R3`, `F-R4` | `R1-R11` |
| Phase 5 | Shared systems and polish | `F-S1`, `F-S2`, `F-S3`, `F-S4`, `F-S5`, `F-S6` | `S1-S14` |

## 3. Recommended First Build Path

Start with the smallest complete loop:

| Step | Feature | Screen IDs | Why First |
| --- | --- | --- | --- |
| 1 | Auth Session | `G1`, `G2`, `G3` | Users must enter the app cleanly |
| 2 | Role Routing | `G4` | App must know where to send a user |
| 3 | Customer Discovery | `C1`, `C2` | First real user demand starts here |
| 4 | Product Commerce | `C3`, `C7`, `C8` | Lets the customer choose supply |
| 5 | Checkout and Payment | `C11` | Starts the transaction |
| 6 | Customer Orders | `C15`, `C16`, `C17` | Closes the MVP customer loop |

## 4. Work Unit Definition

Each team task should be shaped like this:

| Task Part | Requirement |
| --- | --- |
| Feature ID | Example: `F-C2` |
| Screen ID(s) | Example: `C3`, `C7`, `C8` |
| UX source | Which flow doc and screen list it comes from |
| Folder target | Exact folder in `src/features` or `src/shared` |
| Route impact | Which `app/` route file points to it |
| Data needs | Inputs, outputs, and dependencies |

## 5. Team Workflow Per Feature

| Step | What The Team Does |
| --- | --- |
| 1 | Pick a feature from the approved feature set |
| 2 | Read the relevant UX flow doc |
| 3 | Read the matching screen list doc |
| 4 | Confirm screen IDs and data needs |
| 5 | Build inside the owning feature folder |
| 6 | Connect route files in `app/` only after the screen exists |
| 7 | Verify lint, typing, and flow continuity |

## 6. Ownership Model

| Team Area | Owns |
| --- | --- |
| Auth / Entry | `F-G1`, `F-G2` |
| Customer Team | `F-C1` to `F-C6` |
| Vendor Team | `F-V1` to `F-V5` |
| Rider Team | `F-R1` to `F-R4` |
| Shared / Platform Team | `F-G3`, `F-G4`, `F-S1` to `F-S6` |

If the team is small, one person can own multiple areas, but the ownership boundary should still be clear.

## 7. Folder-Level Development Rule

| If You Are Building | Put It In |
| --- | --- |
| One role-specific business flow | its feature folder |
| A role-specific screen helper | that same feature folder |
| A reusable role-agnostic helper | `src/shared/*` |
| Route-level screen file | `app/*` |
| Shared design primitive | `src/shared/ui` |

## 8. Feature Build Sequence

Inside a feature, work in this order:

| Order | Build Item |
| --- | --- |
| 1 | Types and local data contracts |
| 2 | API layer or mock data layer |
| 3 | Hooks and feature logic |
| 4 | Reusable feature components |
| 5 | Feature screen(s) |
| 6 | Route file wiring |

## 9. Example Development Flow

Example for `F-C2 Product Commerce`:

| Step | Action |
| --- | --- |
| 1 | Read `11 - Customer UX Flow.md` |
| 2 | Read `16 - Customer Screen List.md` |
| 3 | Confirm screens `C3`, `C7`, `C8` |
| 4 | Build in `src/features/customer/commerce/` |
| 5 | Add local `types`, `hooks`, `components`, `screens` as needed |
| 6 | Wire `app/(customer)/product-detail.tsx`, `vendor-map.tsx`, `vendor-selection.tsx` |

## 10. Branch / Task Naming Suggestion

| Item | Pattern | Example |
| --- | --- | --- |
| Branch | `feature/<feature-id>-<name>` | `feature/f-c2-product-commerce` |
| Task title | `<feature-id>: <screen-id or area>` | `F-C2: C3 Product Detail` |
| Commit style | `<feature-id> <screen-id>: short action` | `F-C2 C3: add product detail placeholder state` |

## 11. Review Checklist

Before merging a task:

| Check | Question |
| --- | --- |
| Feature ownership | Is the code in the correct feature folder? |
| Screen ownership | Does the screen match the documented screen ID? |
| Shared discipline | Was anything moved to shared too early? |
| Route discipline | Is the route file thin? |
| Flow integrity | Does the new screen lead to the correct next step? |
| Naming consistency | Do file names match the agreed naming rules? |

## 12. Team Sync Routine

| Cadence | Focus |
| --- | --- |
| Before starting a feature | Confirm feature ID, screen IDs, and folder target |
| During build | Raise blockers around data contracts and shared dependencies early |
| Before merge | Compare implementation against UX flow and screen list docs |
| After merge | Update docs only if the agreed flow or ownership changed |

## 13. What Not To Do

| Avoid | Why |
| --- | --- |
| Creating top-level `screens`, `components`, or `services` folders for the whole app again | It breaks the architecture we just defined |
| Building screens without checking their feature and screen IDs | It causes drift and duplicate work |
| Moving code to `shared` because it feels reusable too early | This creates messy shared ownership |
| Putting heavy business logic in `app/` routes | Routes should stay thin and stable |

## 14. Team Starting Pack

Before any feature work starts, every developer should know these docs:

| Doc | Why |
| --- | --- |
| `19 - Feature Definitions.md` | Defines what features exist |
| `20 - ID Key and Naming Conventions.md` | Defines naming and IDs |
| `21 - Architecture and Organization.md` | Defines the structure |
| `22 - Development Flow.md` | Defines how the team should work |
| Relevant role UX flow doc | Gives context for the feature being built |
| Relevant role screen list doc | Gives screen ownership and data needs |

## 15. Final Team Rule

Build in this order:

1. understand the flow
2. identify the feature
3. confirm the screen IDs
4. build inside the owning folder
5. wire the route
6. verify the flow still makes sense
