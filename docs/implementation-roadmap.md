# TIME Protocol Implementation Roadmap

## Phase 0 — Canonical Specification

Goal: make the parent repo the source of truth.

Deliverables:

- core README;
- stablecoin thesis;
- tokenomics specification;
- minting rules;
- governance allocation spec;
- reference app map;
- architecture overview;
- glossary.

## Phase 1 — Minimal Protocol Contracts

Goal: prove the issuance invariant.

Deliverables:

- TIME token contract;
- proof-of-humanity adapter interface;
- birthright claim contract;
- work agreement contract;
- payment-triggered mint function;
- Work NFT contract;
- daily 24 TIME cap;
- basic tests.

Core invariant:

```text
new_TIME_per_human_per_day <= 24
```

## Phase 2 — Governance Agent MVP

Goal: show who governs the user and let them move TIME.

Deliverables:

- location / home jurisdiction claim;
- governance object registry;
- official/law discovery;
- default status-quo allocation;
- support / oppose allocation;
- TIME score dashboard;
- quadratic voting calculation;
- local opportunity feed.

## Phase 3 — Reference App Integration

Goal: connect existing apps to parent protocol.

Deliverables:

- HumanBond TIME integration document;
- Governance Agent integration;
- Logos module spec;
- Network State module;
- jurisdictional pilot template;
- API definitions.

## Phase 4 — Work Marketplace / Local Allocation

Goal: make TIME useful for real work.

Deliverables:

- signed work agreements;
- escrow;
- payment confirmation;
- work verification;
- Work NFT metadata;
- local opportunity marketplace;
- reputation dashboard.

## Phase 5 — Privacy and Selective Disclosure

Goal: prevent TIME from becoming a surveillance ledger.

Deliverables:

- private balances where possible;
- encrypted work metadata;
- selective Work NFT disclosure;
- nullifier-based proof of humanity;
- aggregated governance reporting;
- user export/delete controls where applicable.

## Phase 6 — Jurisdictional Pilot

Goal: deploy TIME in a real community, DAO, network state, or local institution.

Deliverables:

- pilot dashboard;
- verified-human onboarding;
- local public-goods pool;
- governance objects;
- work/payment flows;
- metrics;
- public report.

## Phase 7 — Liquidity and Exchange

Goal: enable TIME to trade without corrupting the human-hour denominator.

Deliverables:

- DEX pool;
- fiat exchange-rate display;
- wage-rate oracles;
- payment asset routing;
- anti-wash-minting rules;
- market risk disclosures.

## Non-Negotiable Invariants

1. One verified human cannot mint more than 24 new TIME/day.
2. Work TIME requires payment.
3. Work events produce non-transferable receipts.
4. Governance power is rooted in verified humans and TIME allocation.
5. TIME is not pegged to the dollar.
6. Privacy must be designed in from the start.
