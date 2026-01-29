# Engineering Decisions Log

This document tracks all engineering decisions made during project development. When decisions change, the original entry is preserved with a "SUPERSEDED" note, and the new decision is added.

---

## How to Use This File

- **New decisions**: Add to the bottom of the relevant category
- **Changed decisions**: Mark the old entry as `[SUPERSEDED]` and add the new decision with a reference to what it replaced
- **Format**: `### Decision Title` → Date → Context → Decision → Rationale

---

## Categories

- [Architecture](#architecture)
- [APIs & Integrations](#apis--integrations)
- [Database](#database)
- [Authentication](#authentication)
- [UI/UX](#uiux)
- [Tooling & DevOps](#tooling--devops)
- [Third-Party Services](#third-party-services)

---

## Architecture

<!-- Example:
### Use Server Components by Default
**Date:** 2024-01-15
**Context:** Needed to decide between client and server components for data fetching
**Decision:** Default to Server Components, use Client Components only when interactivity is needed
**Rationale:** Better performance, simpler data fetching, reduces client bundle size
-->

---

## APIs & Integrations

<!-- Document which APIs are used and why -->

---

## Database

<!-- Schema decisions, indexing strategies, etc. -->

---

## Authentication

<!-- Auth provider choices, session handling, etc. -->

---

## UI/UX

<!-- Component library choices, design system decisions, etc. -->

---

## Tooling & DevOps

<!-- Build tools, CI/CD, deployment choices, etc. -->

---

## Third-Party Services

<!-- External services, payment providers, analytics, etc. -->

---

## Changed Decisions

This section highlights decisions that were later revised. Each entry links to both the original and new decision.

<!-- Example:
### Payment Provider Change
**Date Changed:** 2024-02-01
**Original:** Use Stripe for payments (see [Third-Party Services](#third-party-services))
**New Decision:** Switch to Lemon Squeezy
**Reason for Change:** Better support for international taxes and simpler merchant of record setup
-->
