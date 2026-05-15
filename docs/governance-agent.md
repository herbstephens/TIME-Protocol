# Governance Agent

## Definition

The Governance Agent is a personal AI political and economic advisor for TIME Protocol.

It answers the question:

> Who governs me right now?

Then it lets the user allocate TIME across the people, laws, institutions, budgets, and alternatives that govern their actual life.

## Core Idea

Every human lives inside overlapping jurisdictions:

- neighborhood;
- municipality;
- region/state;
- nation;
- supranational bodies;
- tax authorities;
- courts;
- regulators;
- schools;
- utilities;
- zoning boards;
- employers;
- platforms.

Most people do not know who governs them.

The Governance Agent maps this invisible structure and turns it into an actionable interface.

## Two Numbers

The first UI should be brutally simple:

```text
33 officials govern you.
12,847 laws apply to you.
```

The exact numbers vary by location.

The point is the realization: governance is not abstract. It is local, layered, and continuous.

## Inputs

The agent may use:

- user-claimed home location;
- browser or device location;
- jurisdictional databases;
- official registries;
- election data;
- legislative data;
- court/regulatory data;
- public budget data;
- local opportunity feeds;
- user interests and stated priorities.

## Outputs

The agent produces:

- governing officials;
- relevant laws and ordinances;
- upcoming votes;
- policy changes;
- relevant agencies;
- local businesses and cooperatives;
- public initiatives;
- budget choices;
- governance alternatives;
- recommended TIME allocations.

## Status-Quo Allocation

When a verified human joins, the Governance Agent allocates their governance TIME to the status quo by default.

This means their TIME is initially mapped to:

- current officials;
- current laws;
- current budget categories;
- existing institutions;
- default jurisdictional structures.

The default allocation represents passive consent to the current system.

The user can then move TIME.

## Move TIME = Vote

Moving TIME away from the status quo toward an alternative is the act of voting.

Examples:

- move TIME away from an incumbent mayor toward a challenger;
- move TIME away from a national party toward a local independent;
- move TIME away from a city budget line toward public transit;
- move TIME away from legacy governance toward a network state;
- move TIME toward a cooperative, local institution, or public-good project.

No ballot is required.

The allocation is the preference signal.

## Support and Opposition

For officials and laws, the agent should support both positive and negative allocation.

Example score:

```text
governance_score = support_TIME - oppose_TIME
```

A positive score indicates net support.

A negative score indicates net desire for removal, repeal, replacement, or opposition.

## Quadratic Weighting

Recommended voting function:

```text
votes = sqrt(TIME allocated)
```

This rewards broad participation and discourages domination by concentrated holdings.

## Jurisdictional Scope

The Governance Agent should work for:

- local governments;
- national governments;
- EU or supranational institutions;
- DAOs;
- network states;
- communities;
- cooperatives;
- corporations;
- protocols;
- family/relationship DAOs;
- public goods funds.

## Chain Architecture

Recommended division of labor:

| Layer | Role |
|---|---|
| World ID / Proof of Humanity | one human, one agent |
| NEAR | AI agent persistence, compute, user-owned state |
| EVM / Ethereum / World Chain | TIME token liquidity and verified identity integrations |
| Logos / Waku | private local coordination and jurisdictional messaging |
| Celo or other mobile-first chains | governance experiments and agent registration |

## Governance Agent as Reference App

Governance Agent should be the flagship TIME Protocol application because it connects all protocol layers:

- identity;
- TIME ownership;
- local awareness;
- preference signaling;
- political action;
- public goods allocation;
- network-state legitimacy.

## Product Narrative

> Your Governance Agent shows who governs you, what laws bind you, and where your TIME can move the world.
