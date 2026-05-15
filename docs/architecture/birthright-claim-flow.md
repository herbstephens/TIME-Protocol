# Birthright Claim Flow

## Summary

This file defines the user flow for claiming retroactive and ongoing Birthright TIME.

## Claim Sequence

```text
1. User opens TIME Protocol wallet/app.
2. User verifies humanity.
3. User proves date of birth or days alive.
4. Protocol checks that no prior lifetime claim exists.
5. Protocol calculates retroactive birthright.
6. Protocol records recognized TIME.
7. Protocol releases initial liquid TIME.
8. Protocol activates ongoing daily birthright stream.
9. Protocol enables governance allocation.
```

## Pseudocode

```solidity
function claimRetroactiveBirthright(
    HumanProof proofOfHumanity,
    AgeProof proofOfAge
) external {
    humanId = verifyHuman(proofOfHumanity);
    require(!hasClaimedRetroactive[humanId]);

    daysAlive = verifyDaysAlive(proofOfAge);
    recognizedAmount = daysAlive * 1e18;

    hasClaimedRetroactive[humanId] = true;
    recognizedBirthright[humanId] = recognizedAmount;

    liquidAmount = calculateImmediateLiquidity(recognizedAmount);
    governanceAmount = calculateGovernanceAllocation(recognizedAmount);
    vestingAmount = recognizedAmount - liquidAmount;

    mintLiquidTIME(humanId, liquidAmount);
    creditGovernanceTIME(humanId, governanceAmount);
    createVestingStream(humanId, vestingAmount);
    activateDailyBirthright(humanId);
}
```

## Required Proofs

### Proof of Humanity

Shows that the claimant is a unique living human.

### Proof of Age

Shows the number of days lived or a birth-date commitment sufficient to calculate claim amount.

### Proof of Non-Claim

Shows this human has not previously claimed retroactive birthright.

## Privacy-Preserving Age Proof

The protocol should avoid publishing birthdays.

Possible proof statements:

```text
I am entitled to exactly N days of retroactive birthright.
```

or:

```text
My committed birthdate plus current date produces N claimable days.
```

or, for lower precision:

```text
I am within an age band that produces a bounded claim.
```

## Ongoing Daily Birthright

After retroactive claim, the account becomes eligible for daily birthright.

```text
1 TIME / verified human / day
```

Ongoing birthright may stream continuously or be claimable daily.

## Edge Cases

### Duplicate Claim

Reject claim if human nullifier already used.

### Incorrect Age

Require updated credential or dispute mechanism.

### Lost Wallet

Support recovery through human re-verification and account recovery process.

### Minors

Allow claim to accrue, but restrict liquidity based on policy.

### Custodians

Prevent exchanges, employers, or institutions from mass-claiming on behalf of humans without explicit protections.

## User-Facing Language

> Claim your TIME since birth.

> TIME Protocol recognizes every day you have already lived.

> Your first claim catches you up to now. Your daily birthright continues from here.
