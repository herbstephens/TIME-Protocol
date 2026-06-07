# Tokenomics

**1 TIME = 1 verified hour of human existence. Maximum 24 TIME per person per day.**

---

## Token Parameters

| Parameter | Value | Rationale |
|---|---|---|
| Token name | TIME | Unit of account: verified human hours |
| Standard | ERC-20 (fungible) + ERC-721 (soulbound ProofOfWorkNFT) | Dual-layer: liquid value + reputation record |
| Daily cap | 24 TIME per verified human per day | Hard biological constraint — non-negotiable |
| Daily UBI | 1 TIME/day per verified human | Birthright existence recognition |
| Work TIME max | 23 TIME/day per verified human | Payment-only minting; real work required |
| Retroactive grant | Age × 365 TIME at first verification | Bootstrapping endowment; governance-bound |
| Liquidity unlock | 1:1 with earned work TIME | Anti-speculation; incentive for contribution |
| Partner split | 50/50 via HumanBond for verified partnerships | Recognition of non-market contribution |
| Governance | Quadratic voting with TIME allocation | Anti-whale; democratic weighting |
| Sybil prevention | World ID (Tier 3) for maximum governance weight | Biometric uniqueness verification |

---

## The Three Issuance Streams

### Stream 1: Retroactive Birthright (Age Grant)

```
age_grant = age_in_years × 365

State at verification:
  governance_bound = age_grant   (100%)
  liquid = 0                     (0%)

Unlock mechanism (Liquidity Ladder):
  on_each_work_event(earned):
    unlock = min(earned, remaining_locked)
    governance_bound -= unlock
    liquid += unlock
```

**Why governance-bound first?** Prevents speculation. A 40-year-old verifying today receives ~14,600 TIME — if immediately liquid, this creates sell pressure and speculative behavior that undermines the protocol's economic integrity. Binding it to earned work preserves value while rewarding productive participation.

### Stream 2: Daily UBI (BirthrightClock)

```
daily_ubi = 1 TIME/day per verified human
accrual = continuous (claimable anytime)
source = BirthrightClock.sol (separate contract from work minting)
```

This is the "pass Go" money — the Monopoly analogy. Every verified human, every day, regardless of work status. Funded by the protocol treasury.

### Stream 3: Work TIME

```
work_time_maximum = 23 TIME/day per verified human
mint_trigger = payment_received AND work_verified AND identity_verified
double_booking = prevented by UHTC_Calendar on-chain

HumanBond split (if partnered):
  worker receives: amount / 2
  partner receives: amount / 2
```

**Payment for work is the mint event.** No exceptions. No governance can authorize TIME minting without verified payment.

---

## Supply Model

Total TIME supply is bounded by:

```
daily_supply ≤ Σ(verified_humans) × 24 TIME

More precisely:
  birthright_stream = Σ(verified_days_alive) for all humans (one-time, governance-bound)
  ubi_stream = verified_humans × 1 TIME/day (continuous)
  work_stream = verified_hours × real_paid_demand (payment-triggered)
```

**Three anti-inflation mechanisms:**
1. **Proof of humanity** — Sybil attacks prevented; one human, one calendar
2. **Time exclusivity** — same hour cannot be sold, allocated, or minted twice (UHTC_Calendar)
3. **Payment-based minting** — Work TIME not issued by governance, only by real payment

---

## The Liquidity Ladder

The most important economic primitive for long-term protocol health:

```
// Every time work-backed TIME is earned:
function updateLiquidity(address user, uint256 earned) {
    uint256 remaining = genesisRegistry.getLockedBalance(user);
    uint256 toUnlock = min(earned, remaining);

    totalUnlocked[user] += toUnlock;
    totalEarned[user] += earned;

    governancePool.unlock(user, toUnlock);
    // User now has: earned liquid TIME + toUnlock liquid from Age Grant
}
```

**Result:** A user who performs 500 hours of verified paid work unlocks their first 500 TIME from their birthright endowment. Every unit of productive contribution unlocks an equivalent unit of historical recognition.

---

## Governance Weight and Quadratic Voting

```
voting_power = √(TIME_allocated)

Examples:
  100 TIME → √100 = 10 votes
  400 TIME → √400 = 20 votes  (4× tokens, 2× votes)
  900 TIME → √900 = 30 votes  (9× tokens, 3× votes)
```

Prevents whales from dominating governance. The many can out-vote the few if they collectively care more — regardless of token holdings.

---

## Dollar Stablecoin Comparison

| Property | USD Stablecoin | TIME Protocol |
|---|---|---|
| Reference unit | U.S. dollar (political) | Verified human hour (biological) |
| Stability type | Nominal dollar peg | Human-time parity |
| Backing | Cash, Treasuries, bank reserves | Real payment for verified work |
| Scarcity source | Issuer reserves + regulation | 24 hours/day/human — inviolable |
| Inflation exposure | Inherits USD inflation | Anchored to finite human time |
| Geopolitical neutrality | Low — extends dollar system | High — non-sovereign human unit |
| Trust model | Issuer, custodian, bank, regulators | Proof of humanity + proof of payment |
| Run risk | Redemption and reserve risk | No custodian to run on |

---

*Part of [TIME Protocol](https://github.com/herbstephens/TIME-Protocol)*
*democracy.earth · June 2026*
