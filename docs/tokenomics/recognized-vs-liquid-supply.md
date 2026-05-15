# Recognized Supply vs Liquid Supply

## Summary

Retroactive Birthright TIME creates a large recognized supply.

That does not require the entire amount to become immediately liquid.

The protocol should distinguish between:

1. recognized supply;
2. claimable supply;
3. vested supply;
4. liquid supply;
5. governance-allocatable supply;
6. work-minted supply.

## Why This Distinction Matters

If every verified human receives one TIME per day since birth, total recognized supply will be enormous.

That is economically correct if TIME recognizes lived human days.

But immediate full liquidity could create:

- sell pressure;
- exchange instability;
- capital capture;
- speculative attacks;
- pressure on governance;
- user exploitation.

The solution is not to weaken the birthright.

The solution is to separate recognition from liquidity.

## Suggested Supply Categories

### Recognized TIME

The total amount the protocol acknowledges as belonging to a human based on days lived.

```text
recognized_TIME = days_alive × 1 TIME
```

### Claimable TIME

The amount a human can claim after verification.

In most cases:

```text
claimable_TIME = recognized_TIME
```

### Vested TIME

The portion currently unlocked under vesting rules.

### Liquid TIME

The portion transferable or spendable.

### Governance-Allocatable TIME

The portion usable to express preference, stake to officials, support laws, oppose budgets, or join Shadow Democracy.

### Work-Minted TIME

TIME minted from verified paid work.

## Recommended Accounting

Every account should expose or internally track:

```text
recognized_birthright
liquid_birthright
vesting_birthright
governance_birthright
ongoing_birthright
work_time
```

## Policy Options

### Option 1: Recognition First

The full amount is recognized immediately, but liquidity vests.

### Option 2: Streamed Recognition

The claim exists, but recognition itself streams over time.

### Option 3: Governance First

Most retroactive TIME can be used for governance immediately, but not transferred.

## Recommended Option

Recognition First + Governance First:

```text
100% recognized at verification
meaningful portion liquid immediately
large portion governance-allocatable immediately
remaining portion streams into liquid supply over time
```

## Why Governance Should Unlock Faster Than Liquidity

The purpose of TIME is not merely spending.

It is also human preference signaling.

If retroactive TIME cannot be used for governance, then early governance will be dominated by buyers, builders, and employers.

Governance use should therefore unlock immediately or near-immediately.

## Final Rule

> Recognize all human time. Release liquidity responsibly.
