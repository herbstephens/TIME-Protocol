# Governance Agent — Architecture Specification

> *"Most people do not want to govern. They want things to work."*

---

## Overview

The Governance Agent is AI-assisted governance infrastructure that operates as a **Digital Concierge**: managing community governance in the background for the 90% who simply want things to work, while remaining fully transparent and participatory for the 10% who actively want to engage.

It is not a voting interface. It is not a DAO dashboard. It is the interface through which verified humans assert their time, their preferences, and their governance power against the systems that currently capture all three.

---

## Core Components

### 1. Governance Object Registry (`GovernanceRegistry.sol`)

Any entity or institution that exercises power over a community can be registered as a **Governance Object**:

- Laws and ordinances
- Elected officials
- Budget line items
- Public goods and commons funds
- Community organizations
- Utility infrastructure

**Object types:**
```
enum ObjectType {
    LAW,
    BUDGET,
    OFFICIAL,
    PUBLIC_GOOD,
    ORGANIZATION,
    UTILITY,
    INVESTIGATION  // FraudInvestigation objects
}
```

**Proposal flow:**
1. Any verified human proposes a new Governance Object
2. Community Stewards review for legitimacy
3. Ratification by threshold of verified residents
4. Object indexed to jurisdiction

### 2. Quadratic Allocation Engine (`AllocationManager.sol`)

Verified humans allocate TIME to Governance Objects using **quadratic weighting**:

```
voting_power = Math.sqrt(tokens_locked)

// Examples:
100 TIME locked → √100 = 10 votes
400 TIME locked → √400 = 20 votes (4× tokens, only 2× votes)
900 TIME locked → √900 = 30 votes (9× tokens, only 3× votes)
```

**Why quadratic?** Prevents token-whale capture of governance. The many can out-vote the few if they collectively care more about an issue, regardless of token holdings.

**Allocation properties:**
- TIME is locked during allocation (not spent — remains yours)
- Governance-bound Age Grant counts toward allocation
- Unlock during FraudInvestigation holds (released on resolution)
- Truth Dividend distributed to successful fraud investigators from slashed org bond

### 3. Jurisdiction Mesh (`JurisdictionRegistry.sol`)

Real people participate in multiple governance contexts simultaneously. The Jurisdiction Mesh supports this:

```
// A user's active jurisdictions might include:
[
  { id: "PT-SINTRA", type: "RESIDENCE", label: "Portugal — Sintra/Lisbon" },
  { id: "US-FEDERAL", type: "CITIZENSHIP", label: "United States — Federal" },
  { id: "VOTC-2026", type: "VOLUNTARY", label: "Valley of the Commons 2026" },
  { id: "NETSTATE-01", type: "VOLUNTARY", label: "Network State Node" }
]
```

Users subscribe to multiple jurisdictions. Governance Objects are scoped to jurisdictions. Governance weight is portable across subscriptions.

**Pop-up city / Network State integration:** Temporary jurisdictions can be registered with defined start/end dates. Participants mesh their existing credentials with the temporary grid automatically upon subscription.

### 4. Status-Quo Signal (`GovernanceAgent.sol`)

The Status-Quo Signal shows aggregate TIME allocation across all verified humans in a jurisdiction:

```typescript
interface StatusQuoSignal {
  objectId: string;
  totalTimeAllocated: bigint;
  uniqueAllocators: number;
  weightedVotingPower: bigint;       // Σ √(each allocation)
  supportPercentage: number;         // vs. total jurisdictional governance weight
  userAllocation: bigint;            // this user's contribution
  userDelta: number;                 // user vs. status quo (+ support, - oppose)
}
```

This makes invisible institutional power visible — users see where their preferences align or diverge from the community consensus without requiring expertise in governance.

---

## The Age Grant Allocation Engine

Every newly verified human receives their **Age Grant** (retroactive birthright) as a **Day Zero Governance Endowment**:

```
age_grant = age_in_years × 365 TIME

// Governance-bound at verification:
governance_allocatable = age_grant
liquid = 0

// Unlocks 1:1 as work is earned:
on_work_earned(amount):
  unlock = min(amount, remaining_locked_grant)
  governance_allocatable -= unlock
  liquid += unlock
```

The Governance Agent's first task for a new user: help them understand and allocate this endowment across the Governance Objects that govern their life.

---

## The Local Multiplier

The Local Multiplier measures community economic health:

```
local_multiplier = TIME_circulating_locally / TIME_exported_externally

// Interpretation:
// > 2.0  =  Strong local economy, high resilience
// 1.0–2.0 = Moderate local circulation
// < 1.0  =  Net extraction — community is a feeder for outside interests
```

**Display:** Not as a mandate, but as educational feedback — "x-ray vision" for community economics. Users see how their allocation and spending decisions affect the multiplier in real time.

**Alert threshold:** If multiplier drops below community-set minimum, Governance Agent surfaces a Yellow alert to residents with context and options.

---

## The AI Layer

The Governance Agent uses AI for two functions:

### Jurisdictional Mapping
Determines which Governance Objects are relevant to a specific user based on their jurisdiction subscriptions, historical activity, and stated preferences. Reads from `JurisdictionRegistry` and `GovernanceRegistry`.

### Allocation Assistance
Suggests allocation strategies consistent with the user's Governance Charter — a JSON-LD document encoding their governance principles:

```json
{
  "@context": "https://timeprotocol.org/governance-charter/v1",
  "@type": "GovernanceCharter",
  "subject": "did:world:{nullifier}",
  "principles": {
    "anti_extractive": true,
    "local_first": true,
    "minimum_local_multiplier": 1.5
  },
  "thresholds": {
    "auto_allocate_below": 100,
    "require_confirmation_above": 1000,
    "emergency_override": true
  },
  "delegations": {
    "default": "community_steward_pool",
    "override_on_alert": "self"
  }
}
```

**Model-agnostic:** The Charter is the source of truth. Any AI model (Claude, Gemini, local model) can parse and execute the Charter. Swapping the AI model does not affect governance history or credential state.

**Audit ledger:** All AI-assisted governance decisions are hashed and stored on Soroban. Full transparency: reasoning, proposed action, user approval or override — all on-chain.

---

## User Experience: Three States

### 🟢 Green — Everything functioning
- No action required from user
- Weekly summary: service performance, budget utilization, Local Multiplier score
- 90% of users live here permanently

### 🟡 Yellow — Attention needed
- Anomaly detected or governance decision approaching ratification threshold
- User notified with context: what's happening, options, Steward recommendation
- Can ratify, oppose, or re-delegate

### 🔴 Red — Critical incident
- Community attention required
- Full data, proposed responses, clear call to action
- Rare by design — Constitutional Immutables and automated monitoring prevent most red states

---

## Community Stewards

Stewards are the human layer between automated systems and full community votes:

**Election:** TIME-weighted quadratic vote. Fixed, non-renewable terms.

**Authority:** Handle decisions too frequent for full community votes but too important to automate.

**Constraints:**
- Financially bonded (TIME bond slashed on malfeasance)
- Geographically distributed (must represent jurisdiction diversity)
- Transparent record (every decision logged on-chain)
- Subject to recall by supermajority at any time

**Steward decisions that require full community ratification:**
- Structural changes to utility governance
- Constitutional amendments
- Anything affecting service access for whole community

---

## Deployment: Soroban (Stellar)

The Governance Agent is being built on Soroban for three reasons:

1. **Fee accessibility** — governance actions must be economically viable for a verified human in Lagos as much as Lisbon
2. **Cross-border settlement** — JurisdictionRegistry handles TIME allocation across multiple currency and legal jurisdictions via Stellar's path payment system
3. **Regulatory posture** — engagement with governments, NGOs, and international organizations requires Stellar's compliance-friendly reputation

**Target deployment:** Q4 2026 (pending SCF Build Award — see [`/docs/scf/scf-build-award.md`](../scf/scf-build-award.md))

---

## Valley of the Commons Pilot

The Austrian Alps pop-up community (Governance Week 2026) is the first live deployment:

- Jurisdiction: `VOTC-2026` registered in JurisdictionRegistry
- Governance Objects: communal kitchen budget, shared workspace, energy pool, tooling commons
- Tiered ID: World ID (Apex) for existing verified users; Passport NFC and peer vouching for new participants
- Local Multiplier: live measurement of TIME circulation within the village vs. external leakage
- Herb Stephens attending Governance Week only

**Post-pilot deliverable:** "Pop-Up City in a Box" toolkit — documented, modular, ready for any community to deploy.

---

*Part of [The Great Reset](https://github.com/herbstephens/The-Great-Reset) repository*
*democracy.earth · June 2026*
