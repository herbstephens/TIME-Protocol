# Reputation Score — Specification

**Five-dimensional. Identity-attached. Soulbound. Selectively disclosed.**

---

## Overview

Every verified human in the TIME Protocol accumulates a multi-dimensional Reputation Score attached directly to their **World ID identity** — not their wallet, not their resume, not a platform account.

The score is:
- **Permanent** — on-chain, immutable activity history
- **Portable** — follows the human across wallet changes, devices, and protocols
- **Composable** — any application can read any dimension
- **Private** — the human controls what each verifier sees via ZK proofs

---

## The Five Dimensions

| Dimension | Source | What it captures |
|---|---|---|
| **Work Reputation** | `ProofOfWorkNFT` history | Paid work volume, consistency, counterparty diversity, industry spread, recency weighting |
| **Civic Reputation** | `VolunteerPROOF` NFTs | Volunteer hours by org type, early vs. late supporter timing, role specificity, election outcomes, jurisdictional breadth |
| **Governance Reputation** | Governance Agent allocation history | Participation frequency and consistency, jurisdictional diversity, quadratic vote deployment |
| **Partnership Reputation** | HumanBond / Partnership Registry | Formation and duration, dissolution record, 50/50 income participation |
| **Identity Tier** | Tiered Humanity Stack | Verification depth (Tier 0–3); modulates all other dimensions |

**Scoring:** Each dimension returns a score 0–1000. Identity Tier is a multiplier (Tier 0 = 0.5×, Tier 3 = 1.0×) applied to all other dimensions.

---

## Architecture: Three Design Principles

### 1. Soulbound — Cannot be transferred or gamed

Every NFT feeding the Reputation Score is non-transferable. Changing wallets does not reset reputation — World ID is the anchor. A user cannot buy reputation from another wallet or sell their history.

### 2. Identity-Attached — Follows the human, not the wallet

The `ReputationRegistry` maps scores to **World ID nullifiers** — privacy-preserving unique identifiers from the World ID ZK proof system. Wallet rotation for security reasons does not affect reputation. Cross-chain activity aggregates under the same identity.

### 3. Selectively Disclosed — The human controls the lens

ZK proofs at the application layer enable granular selective disclosure:

```
// A volunteer can prove:
"I have 200+ verified volunteer hours for a Democratic primary campaign
 in the 2026 election cycle"
// Without revealing: which campaign, which candidate, wallet address,
//                   income history, or any other dimension
```

```
// An employer can verify:
"This applicant's Work Reputation score exceeds threshold 700"
// Without seeing: counterparty names, income amounts, or other work details
```

---

## ReputationRegistry Contract

```solidity
interface IReputationRegistry {
    // Individual dimension queries
    function getWorkScore(bytes32 worldIdNullifier)
        external view returns (uint256 score, uint256 lastUpdated, uint256 totalHours);

    function getCivicScore(bytes32 worldIdNullifier)
        external view returns (uint256 score, CivicBreakdown memory breakdown);

    function getGovernanceScore(bytes32 worldIdNullifier)
        external view returns (uint256 score, uint256 participationFrequency, bytes32[] memory activeJurisdictions);

    function getPartnershipScore(bytes32 worldIdNullifier)
        external view returns (uint256 score, PartnershipStatus status, uint256 durationDays);

    function getIdentityTier(bytes32 worldIdNullifier)
        external view returns (uint8 tier, VerificationMethod[] memory methods, uint256 lastVerified);

    // Full profile — gated by ZK disclosure proof from identity holder
    function getFullProfile(bytes32 worldIdNullifier, bytes calldata disclosureProof)
        external view returns (ReputationProfile memory profile);

    // Threshold verification — MOST COMMERCIALLY IMPORTANT
    // Returns boolean only — no underlying data exposed
    function verifyThreshold(
        bytes32 worldIdNullifier,
        Dimension dimension,
        uint256 minimumScore
    ) external view returns (bool meetsThreshold);
}
```

### The `verifyThreshold()` Function

This is the primary commercial primitive. It allows any application to gate access by reputation score without receiving any raw data.

**Examples:**
- Dating platform gates premium features by Civic Reputation score
- Employer requires Work Reputation above 700 for job applications
- DAO requires Governance Reputation above 500 for proposal rights
- Financial service requires Partnership score for joint account eligibility

None of these require exposing the underlying data — only a boolean response.

---

## Civic Reputation: Political Campaigns in Detail

The Civic Reputation dimension captures the most politically and professionally sensitive contribution a citizen can make. Each `VolunteerPROOF` NFT contributes:

```typescript
interface CivicBreakdown {
    totalHours: number;
    hoursByOrgType: {
        POLITICAL_CAMPAIGN: number;
        NONPROFIT: number;
        MUTUAL_AID: number;
        GOVERNMENT: number;
        // ...
    };
    earlySupporter: {
        ratio: number;           // % of hours in first half of campaign duration
        significantContrib: boolean; // 50+ hours in first 20% of campaign duration
    };
    outcomeRecord: {
        won: number;
        lost: number;
        pending: number;
    };
    roles: {
        FIELD_ORGANIZING: number;
        CANVASSING: number;
        PHONE_BANKING: number;
        // ...
    };
    jurisdictions: string[];     // Electoral districts, states, nations
    cycles: string[];            // '2024-primary', '2026-general', etc.
}
```

**The `earlySupporter.ratio` is the single most distinctive Civic Reputation metric.** It captures the timing dimension that no resume can capture: conviction vs. bandwagon participation. High ratio = early believer. Low ratio = late-stage joiner. Immutable. On-chain.

---

## Work Reputation: Informal Workers

The Work Reputation dimension is particularly transformative for the 1.4 billion workers globally in informal employment — no payslips, no tax records, no verifiable employment history.

A domestic worker paid through TIME contracts for five years has a verifiable, portable work history that no bank, landlord, or visa officer currently has access to. VolunteerPROOF and ProofOfWorkNFT together give informal workers their first formal credential.

**Work Reputation components:**
- Total verified hours (by time period and category)
- Counterparty diversity (how many distinct organizations have paid — proxy for market validation)
- Income consistency (sporadic vs. continuous — relevant for underwriting)
- Industry spread (inferred from OrganizationRegistry tags)
- Recency weighting (recent work weighted more than distant — living credential, not static snapshot)

---

## Reputation as Bridge to Real World

The Reputation Score is the mechanism by which TIME Protocol becomes legible to institutions that will never interact directly with a blockchain.

An immigration officer reviewing a residency application does not need to understand World Chain. They need a verifiable document: *"This person has 1,200 verified work hours over 3 years, a Civic Reputation score of 847, and a Partnership status of partnered since 2022."*

The ReputationRegistry generates that document — cryptographically signed, verifiable by any institution with a QR reader.

> *"Your reputation is the sum of your verified contributions to others. For the first time, it is also portable."*

---

## Implementation Status

| Component | Status |
|---|---|
| ReputationRegistry contract spec | ✅ Complete |
| Work Reputation (ProofOfWorkNFT source) | 🔨 In development |
| Civic Reputation (VolunteerPROOF source) | 🔨 In development |
| Governance Reputation (GovernanceAgent source) | 🔨 In development |
| Partnership Reputation (HumanBond source) | ✅ HumanBond live |
| Identity Tier (World ID source) | ✅ World ID live |
| ZK selective disclosure layer | 📋 Specified |
| verifyThreshold() commercial API | 📋 Specified |

---

*Part of [The Great Reset](https://github.com/herbstephens/The-Great-Reset) repository*
*democracy.earth · June 2026*
