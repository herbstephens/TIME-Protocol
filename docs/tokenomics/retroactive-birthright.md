# Retroactive Birthright TIME

## Summary

Retroactive Birthright TIME is the initial allocation granted to a verified human when they first join the protocol.

It is calculated at a rate of:

```text
1 TIME / day since birth
```

The purpose is to make the TIME Protocol universal from inception by recognizing that human time existed before the protocol did.

## Core Principle

TIME Protocol should not act as if value begins at protocol launch.

Every human has already lived through days, years, and decades of scarce time.

Retroactive Birthright TIME recognizes this fact.

## Canonical Formula

```text
retroactive_birthright_TIME = days_alive × 1 TIME
```

Where:

```text
days_alive = floor(current_timestamp - verified_birth_timestamp) / 1 day
```

Example:

```text
A 30-year-old verified human has lived approximately 10,957 days.

Initial retroactive birthright allocation:
10,957 TIME
```

## Why It Exists

Retroactive Birthright TIME solves five launch problems.

### 1. Fair Genesis

Without retroactive allocation, the first holders of TIME would be buyers, investors, insiders, employers, or early technical users.

That would reproduce the capital-first logic TIME is designed to replace.

Retroactive allocation makes humanity the genesis class.

### 2. Universal Monetary Bootstrapping

A monetary system cannot function if users begin with zero.

Retroactive Birthright TIME gives every verified human starting currency, just as a game gives each player starting money.

### 3. Recognition of Lived Time

The protocol does not create human time. It recognizes it.

A person who verifies today has still lived every day before today.

### 4. Global Inclusion

A person should not be disadvantaged because they learned about the protocol late, lacked internet access, lacked a wallet, or lived outside early-adopter geographies.

### 5. Moral Coherence

If TIME claims that human time is the base unit of value, it must recognize all humans' lived time, not merely the time occurring after contract deployment.

## Monopoly Analogy

In Monopoly, players receive money before play begins.

Without starting money, the game cannot function.

Then, when players pass Go, they receive additional money because they completed a full cycle around the board.

TIME Protocol maps this as:

| Monopoly | TIME Protocol |
|---|---|
| Starting cash | Retroactive Birthright TIME |
| Passing Go | Daily birthright issuance |
| Full trip around board | Passage of time |
| Buying property | Allocating TIME to work, governance, local opportunities |
| Rent flows | Economic settlement |
| Bank | Protocol issuance rules |

The crucial insight:

> A new system needs currency in the hands of all players before meaningful play can begin.

## Difference from Work TIME

Retroactive Birthright TIME is not earned.

It is not compensation for completed work.

It is not a wage.

It is a recognition of lived human time.

Work TIME remains payment-backed and should preserve the rule:

```text
Payment for work is the mint event.
```

## Issuance Categories

Recommended accounting fields:

```text
retroactive_birthright_time
ongoing_birthright_time
work_time
volunteer_time
bond_time
governance_time
```

This allows the protocol to preserve the clean definition of each mint source.

## Transferability

There are three possible models.

### Model A: Fully Transferable

Retroactive Birthright TIME is immediately fungible with all TIME.

Advantage:

- maximum liquidity;
- simple user experience;
- strong universal launch.

Risk:

- immediate selling pressure;
- accumulation by capital holders;
- weakens governance if wealthy buyers absorb supply.

### Model B: Vested Transferability

Retroactive Birthright TIME vests over time.

Example:

```text
10% liquid immediately
90% streams over 10 years
```

Advantage:

- prevents one-time dump;
- preserves long-term participation;
- supports stable launch.

Risk:

- feels less like full recognition;
- more complex.

### Model C: Split Liquid / Governance

Retroactive Birthright TIME is split into:

```text
liquid_TIME
governance_TIME
```

Liquid TIME can be spent or transferred.

Governance TIME can be allocated but not sold.

Advantage:

- gives every human immediate voice;
- reduces capital capture;
- preserves monetary liquidity.

Risk:

- creates more token classes.

## Recommended Launch Design

The strongest balanced model:

```text
Retroactive Birthright TIME is claimable at verification.
A portion becomes liquid immediately.
A portion streams continuously as ongoing personal liquidity.
A portion may be usable immediately for governance allocation.
```

This gives every human:

1. money to use;
2. governance voice;
3. long-term participation;
4. protection against one-time extraction.

## Verification Requirements

Retroactive claims require:

1. proof of humanity;
2. proof of uniqueness;
3. proof or attestation of birth date;
4. anti-duplication nullifier;
5. one lifetime retroactive claim.

## Birth Date Verification

Possible methods:

- government ID;
- passport;
- birth certificate;
- national identity systems;
- privacy-preserving credential;
- World ID plus age attestation;
- zero-knowledge proof of date-of-birth range;
- trusted issuer attestation.

## Privacy Principle

The protocol does not need to expose a user's birthday publicly.

It needs a valid proof of days alive.

Recommended model:

```text
prove(days_alive >= N) or prove(exact claim amount) without exposing raw birthdate
```

## Fraud Risks

Retroactive Birthright TIME introduces serious attack surfaces:

- fake identities;
- duplicate humans;
- false ages;
- forged birth records;
- deceased-person claims;
- coercive claiming;
- institutional capture;
- claims by custodial wallets;
- birthdate privacy leaks.

## Anti-Fraud Controls

Recommended controls:

- proof of humanity;
- one nullifier per human;
- privacy-preserving birth-date credential;
- delayed full liquidity;
- claim monitoring;
- guardianship rules for minors;
- recovery rules;
- death/inactivity handling;
- no custodial mass-claiming without safeguards.

## Minors

Minors raise a special design question.

Possible rule:

```text
Retroactive Birthright TIME accrues from birth but cannot be fully transferred until legal adulthood or guardian-controlled rules are satisfied.
```

## Deceased Humans

Retroactive birthright should generally be claimable only by living verified humans.

If inheritance is later introduced, it should be treated as a separate legal and protocol module.

## Economic Implications

Retroactive Birthright TIME creates a very large initial supply.

That is not a bug.

It is the point.

The protocol is not pretending human time began at launch.

However, liquidity and governance rules must prevent the initial supply from being captured by capital markets.

## Key Distinction

The total recognized supply and the liquid circulating supply do not need to be identical.

Recommended accounting:

```text
recognized_TIME_supply
vested_TIME_supply
liquid_TIME_supply
governance_allocatable_TIME
work_minted_TIME
```

## Public Narrative

> TIME Protocol launches by recognizing every day every human has already lived.

## Canonical Statement

> The protocol does not mint history. It acknowledges it.
