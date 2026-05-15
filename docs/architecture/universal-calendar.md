# Universal Calendar

## Summary

The Universal Calendar is a core TIME Protocol primitive.

It enforces the biological fact that each verified human has only 24 hours per day.

## Purpose

The Universal Calendar prevents double-booking, double-selling, or double-minting the same human hour.

## Core Invariant

```text
A verified human cannot allocate the same hour twice.
```

## Slot Model

A simple model divides each UTC day into 24 hourly slots.

```text
human_id
date
hour_0 ... hour_23
```

Each slot may be:

- free;
- reserved;
- completed;
- disputed;
- expired;
- minted;
- cancelled.

## Why Soulbound

A calendar should be bound to a verified human.

It should not be transferable.

The calendar represents capacity, not property.

## Relationship to TIME Minting

A work mint requires:

1. verified human;
2. available calendar slot;
3. reservation;
4. work agreement;
5. completion or acceptance;
6. payment;
7. minting;
8. Work NFT receipt.

## Birthright TIME

Birthright TIME may not require booking all slots.

However, all issuance must still respect the daily cap:

```text
birthright_TIME + work_TIME + app_specific_TIME <= 24
```

## Privacy

The calendar must not become a surveillance tool.

Recommended privacy model:

- public proof that no overlap occurred;
- private underlying schedule;
- encrypted metadata;
- selective disclosure to counterparties;
- zero-knowledge proof of availability when possible.

## Open Questions

- Should slots be strictly hourly or support fractional time?
- Should all slots use UTC or local jurisdictional time?
- Can a user pre-commit future time?
- How are cancellations handled?
- How are disputes handled?
- Can sleep, care, relationship, or civic time be represented separately?
- Should AI-assisted work count differently from manual work?

## Recommended Initial Implementation

Start simple:

```text
24 UTC slots per verified human per day.
No overlapping reservations.
Mint only after payment and completion.
```
