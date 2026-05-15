# Shadow Democracy

## Definition

Shadow Democracy is the TIME Protocol governance layer.

It is a parallel political system that maps every verified human's TIME allocation across the officials, laws, institutions, budgets, and alternatives that govern their life.

It does not wait for formal elections.

It runs continuously.

## Core Mechanism

```text
Claim TIME → allocate to status quo → move TIME to express preference
```

The user begins with a default allocation to the current governance structure.

Then the user moves TIME.

That movement is the vote.

## Why "Shadow"

Shadow Democracy does not immediately replace legal democracy.

It shadows it.

It creates a real-time, on-chain, human-verified preference map running beside existing institutions.

It can show:

- where legitimacy is flowing;
- which officials have lost consent;
- which laws lack support;
- which budgets people actually want;
- which alternatives are gaining traction.

## Default Status-Quo Allocation

By default, governance TIME is allocated to the current system.

This is important because it makes the model conservative at rest.

Nothing changes until humans move their TIME.

Default allocation can be weighted by:

- jurisdictional tier;
- authority level;
- budget share;
- legal impact;
- user's claimed home location;
- optional personal priorities.

## Moving TIME

Moving TIME can express:

- support;
- opposition;
- recall preference;
- budget preference;
- law repeal preference;
- replacement preference;
- network-state allegiance;
- public-goods priority;
- local allocation preference.

## Supported Governance Objects

TIME may be allocated to:

- people;
- laws;
- budgets;
- agencies;
- jurisdictions;
- courts;
- regulators;
- political parties;
- proposed reforms;
- initiatives;
- public goods;
- network states;
- DAOs;
- local institutions.

## Governance Object Identifier

Every governance object should have a deterministic identifier.

Example:

```text
governance_object_id = hash(type, name, jurisdiction, role, source_registry_id)
```

Examples:

```text
official:mayor:lisbon:2026
law:portugal:tax-code:article-x
budget:sintra:public-transit:2026
network-state:time-dao
```

## Vote Accounting

Basic formula:

```text
support_score = sum(sqrt(TIME allocated in support))
oppose_score  = sum(sqrt(TIME allocated in opposition))
net_score     = support_score - oppose_score
```

## Preference Signal vs Legal Vote

Shadow Democracy is not initially a legal election system.

It is a preference protocol.

It becomes politically powerful when:

- enough humans participate;
- jurisdictional coverage becomes credible;
- officials monitor their TIME scores;
- media reports legitimacy flows;
- network states use it as census and mandate evidence;
- governments adopt it for consultation, recall, budgeting, or referenda.

## Network-State Legitimacy

A network state can register as a governance alternative.

Its legitimacy is measured by how much verified human TIME moves toward it.

This becomes a cryptographic census:

```text
verified humans × allocated TIME × jurisdictional distribution
```

## Design Goal

The goal is not token governance.

The goal is human governance using TIME as a scarce, earned, identity-bound signal of attention, work, and preference.
