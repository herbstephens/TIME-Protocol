# TIME Tokenomics Specification

## Core Unit

```text
1 TIME = 1 verified hour of human productive capacity
```

TIME is not pegged to the U.S. dollar. TIME is denominated in the verified human hour.

## Issuance Categories

TIME has two primary issuance categories:

1. **Birthright TIME**
2. **Work TIME**

### Birthright TIME

Birthright TIME is a protocol-level UBI allocation for verified humans.

Recommended current baseline:

```text
1 TIME / verified human / day
```

Possible future expansion:

```text
2 TIME / verified human / day
```

Birthright TIME represents the social minimum: no verified human starts from zero in the TIME economy.

### Work TIME

Work TIME is minted when a verified human performs contracted work and receives payment.

Recommended cap:

```text
Up to 23 earned TIME / verified human / day
```

Combined with 1 birthright TIME/day, this preserves the 24-hour biological maximum.

## Daily Ceiling

```text
Birthright TIME + Work TIME <= 24 TIME / verified human / day
```

This is the core monetary invariant.

No identity can mint, earn, claim, or receive newly issued TIME above the daily biological ceiling.

## Minting Rule

```text
Payment for work is the mint event.
```

TIME should be minted only when the protocol verifies:

1. unique human identity;
2. non-overlapping time allocation;
3. signed work agreement;
4. payment received;
5. work completion, acceptance, or contractual satisfaction.

## Supply Formula

The theoretical maximum daily issuance is:

```text
verified humans × 24 TIME/day
```

The practical daily issuance is:

```text
verified humans × (birthright allocation + verified paid work)
```

## Scarcity Model

TIME scarcity is biological.

Fiat scarcity is political.  
Bitcoin scarcity is mathematical.  
Gold scarcity is geological.  
TIME scarcity is biological.

## Work-Backed Issuance

The strongest monetary claim is not that TIME is backed by labor in the abstract.

The stronger claim is:

> TIME is backed by market-clearing payment for verified human work.

A self-reported hour does not create TIME. A paid, verified, non-overlapping human hour does.

## Dual Representation

Each work-earned unit of TIME should have two parallel records:

| Layer | Instrument | Purpose |
|---|---|---|
| Money | ERC-20 / fungible TIME | Liquid, transferable, spendable |
| Record | Soulbound Work NFT | Permanent proof of the specific verified work event |

The fungible token is money.

The soulbound NFT is the receipt.

## Transferability

Birthright and work-earned TIME may be fungible and transferable unless a specific application requires restrictions.

Work NFTs should be non-transferable.

## Privacy

TIME balances, work records, and identity links should be privacy-preserving by default.

Recommended design:

- public proof of valid minting;
- private work metadata;
- selective disclosure of Work NFTs;
- zero-knowledge proof of personhood;
- nullifier-based anti-Sybil protection;
- optional jurisdiction disclosure for governance/tax use cases.

## Governance Power

TIME can be staked or allocated to governance positions.

Recommended voting formula:

```text
votes = sqrt(TIME allocated)
```

Quadratic weighting rewards breadth of participation and reduces the influence of concentrated token holdings.

## Monetary Claim

TIME should not claim a fixed fiat price.

The canonical claim is:

> 1 TIME always represents 1 verified human hour; fiat exchange rates may float.
