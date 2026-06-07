# HumanBond — Architecture Specification

**Live on World Chain Mainnet · Live in World App Store**

---

## What It Is

HumanBond is the two-person partnership protocol built on TIME. It enables any two verified humans to formalize a time commitment on-chain — romantic partners, business co-founders, co-parents, or long-term collaborators.

HumanBond is not a marriage app. It is a **two-party time commitment infrastructure** — deliberately civic and neutral in framing, applicable to any verified human partnership regardless of legal status, jurisdiction, or relationship type.

---

## Live Deployments (World Chain Mainnet)

| Contract | Address |
|---|---|
| HumanBond | `0x6494daa4e693F748Eb0a16041ECfCEd51392bB13` |
| TIME Token (ERC-20) | `0x261f6d89491cbadff7813303363a514f4b226a82` |
| VowNFT (ERC-721) | `0xa1650cc531c2780fb8c006f4b8d314018f7f9ac9` |
| MilestoneNFT (ERC-721) | `0x0a2759241d0cb610e3e61db351813ddf8a52f14c` |

**Mini App:** Live in World App store. Search: `HumanBond`

---

## Core Mechanics

### Partnership Formation
```solidity
// Two-step process requiring both parties
proposePartnership(address partner, bytes calldata worldIdProof)
confirmPartnership(uint256 proposalId, bytes calldata worldIdProof)
```

Both partners must be World ID verified. Formation mints a `VowNFT` to each partner — soulbound, non-transferable proof of the on-chain commitment.

### The 50/50 TIME Split
When one partner earns work-backed TIME through the protocol, the split is automatic:

```solidity
function finalizeWorkAndDistribute(address worker, uint256 amount) external {
    uint256 half = amount / 2;
    timeToken.mint(worker, half);

    address partner = bonds[worker].partner;
    if (partner != address(0)) {
        timeToken.mint(partner, half);
    }
}
```

**Why this matters:** This formally recognizes the economic contribution of domestic, caregiving, and non-market work — a recognition that existing financial systems consistently fail to provide. The non-working partner in a recognized HumanBond receives TIME automatically, without requiring them to prove or perform paid labor.

### Dissolution
```solidity
dissolvePartnership(uint256 bondId)
// One-click. Callable by either party. Immediate upon confirmation.
// VowNFT marked dissolved. No judicial process required.
```

### Milestone Recognition
```solidity
mintMilestoneNFT(uint256 bondId, string calldata milestoneType, bytes calldata metadata)
// Commemorates significant events: first year, major decisions, achievements
// Soulbound — permanent record of partnership history
```

---

## The Partnership Registry

The HumanBond DAO maintains the **Partnership Registry** — a permanent, tamper-proof on-chain record of verified two-person partnership states.

This registry is one of HumanBond's most commercially significant outputs.

### The Problem It Solves

Dating platforms, social networks, and professional services face a persistent, costly problem: users misrepresenting their relationship status. A verified human in a registered HumanBond partnership cannot credibly claim to be single — their status is publicly verifiable on World Chain.

### The Partnership Status API

```typescript
// Single lightweight call
getPartnershipStatus(worldIdAddress: string): {
  status: 'SINGLE' | 'PARTNERED' | 'PENDING' | 'DISSOLVED',
  since: timestamp | null,
  dissolvedAt: timestamp | null
}
```

**What it exposes:** Binary status + timestamps. Nothing else.

**What it does NOT expose:** Partner identity, personal data, relationship details, income history, or any other private information.

**Verification type:** Cryptographic, not self-reported. The status is on-chain and unalterable by the user without their partner's participation.

### Commercial Applications

| Vertical | Use case | Value |
|---|---|---|
| **Dating platforms** (Tinder, Match, Hinge, Bumble) | Verify user is not in registered partnership before allowing matching | Reduces fraud, improves trust, defensible compliance posture |
| **Professional networks** | Verify relationship status claims without self-attestation | Credibility without privacy invasion |
| **Financial services** | Verify partnership for joint accounts, insurance, beneficiary designations | Eliminates certificate submission; cryptographic proof |
| **Legal services** | Proof of partnership formation or dissolution date | Immutable timestamp for jurisdiction-specific proceedings |
| **Immigration / residency** | Verifiable evidence of partnership for spousal visa applications | Cryptographic proof without requiring government certificate |

### Revenue Model

Platforms pay a per-query fee or subscription. Revenue flows to the HumanBond DAO treasury, funding ongoing development and governance.

Network effect: more platforms adopting the API → more valuable for users to register their partnership → more World ID verification → stronger sybil resistance across the ecosystem.

> *"Self-reported relationship status is a lie waiting to happen. Cryptographically verified partnership status on a public ledger is not."*

---

## Identity Requirements

| Action | Minimum tier required |
|---|---|
| View partnerships | None (public registry) |
| Propose partnership | World ID (Tier 3) — both parties |
| Confirm partnership | World ID (Tier 3) — both parties |
| Dissolve partnership | World ID (Tier 3) — either party |
| Earn split TIME | World ID (Tier 3) for working partner |
| Receive split TIME | World ID (Tier 3) for receiving partner |

---

## ETHGlobal Lisbon (July 24–26, 2026)

HumanBond is the lead application for ETHGlobal Lisbon. New features being built at the hackathon:

1. **TIME income split** — live 50/50 split on work payment (Leticia, pre-hackathon)
2. **Age Grant visualization** — retroactive birthright display + Liquidity Ladder (Franco, at hackathon)
3. **Governance Agent UI** — quadratic allocation dashboard (Franco, at hackathon)

**Prize tracks:** World ID (Best Overall Use Case), World Chain (Best Deployed App), AI+Crypto track.

**Demo close line:** *"Bitcoin is proof-of-work for machines. TIME is proof-of-work for humans. HumanBond is the first app that makes that real."*

---

## Relationship to TIME Protocol

HumanBond is a **reference application** built on TIME Protocol. It demonstrates:

- TIME as a wage stablecoin (50/50 split on work payment)
- Partnership Registry as a commercial primitive (B2B API)
- World ID integration as identity layer
- Soulbound NFTs as reputation layer (VowNFT, MilestoneNFT)

The TIME Protocol is the infrastructure. HumanBond is the first application.

---

*Part of [The Great Reset](https://github.com/herbstephens/The-Great-Reset) repository*
*democracy.earth · June 2026*
