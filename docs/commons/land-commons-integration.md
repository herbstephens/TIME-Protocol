# Land Commons Integration

## Summary

Land Commons is a complementary module to TIME Protocol.

It should not be merged into TIME token issuance.

Instead, it should be treated as a separate commons-dividend system that can use TIME Protocol identity and distribution infrastructure.

## Core Claim

TIME Protocol governs human time.

Land Commons governs land value.

They are related but distinct.

## Separation of Units

| System | Unit | Source | Distribution |
|---|---|---|---|
| TIME Protocol | TIME | verified human time and paid work | birthright / earned work / app rules |
| Land Commons | Commons Dividend | land-use fees | equal distribution to verified humans |

## Why Separate Them

If Land Commons dividends are collapsed into TIME issuance, TIME risks losing its clean monetary definition:

```text
1 TIME = 1 verified hour of human productive capacity
```

Land dividends should instead be distributed as:

- stablecoins;
- local currency;
- ETH;
- WLD;
- a separate Commons token;
- or claimable purchasing power routed through the CommonsDistributor.

## Land Commons Model

The Great Reset repo describes:

- land enters a shared commons;
- structures remain private property;
- fees are collected based on automated land valuation;
- dividends are distributed equally to verified humans.

## TIME Integration Points

Land Commons can use TIME infrastructure for:

1. proof of humanity;
2. equal per-human dividend eligibility;
3. jurisdictional mapping;
4. Governance Agent display;
5. local allocation of dividends;
6. commons treasury governance;
7. anti-Sybil protection;
8. public-goods routing.

## Governance Agent Role

The Governance Agent can show:

- land parcels in the user’s jurisdiction;
- assessed commons fees;
- local dividend pool;
- public-goods uses;
- governance votes on land policy;
- allocation choices.

## Contract Architecture

Recommended contracts:

```text
LandRegistry.sol
LandValuationOracle.sol
CommonsDistributor.sol
JurisdictionRegistry.sol
VerifiedHumanRegistry.sol
```

`CommonsDistributor` should depend on verified humanity but should not mint TIME unless a separate rule explicitly converts a portion of land dividend into TIME-denominated public work.

## Design Principle

> The earth belongs to everyone. Your work belongs to you. Your time has value.

Land Commons expresses the first clause.

TIME Protocol expresses the second and third.
