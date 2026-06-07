# TIME Protocol — Project Map

TIME Protocol is the parent economic protocol. All surrounding repositories are reference applications, implementation modules, and jurisdictional pilots built on top of it.

---

## The Protocol Stack

TIME Protocol is a stack, not a single app:

| Layer | What it does |
|---|---|
| **1. Identity** | One verified human, one time account. Tiered Humanity Stack (Tier 0 peer vouching → Tier 3 World ID biometric). |
| **2. Economy** | TIME token, work contracts, payment-triggered minting, Daily UBI, Retroactive Birthright, Liquidity Ladder. |
| **3. Records** | Soulbound Work NFTs, VolunteerPROOF NFTs, VowNFTs — immutable reputation layer. |
| **4. Governance** | Governance Agent: status-quo allocation, quadratic voting, jurisdiction mesh, Local Multiplier. |
| **5. Partnership** | HumanBond: two-person time commitment, 50/50 income split, Partnership Registry API. |
| **6. Civic** | VolunteerPROOF: civic contribution credentialing, political campaign records, organization bonding. |
| **7. Utility** | Utility Concierge: community utility governance, anti-authoritarian infrastructure, five persistence mechanisms. |
| **8. Jurisdictions** | Network States, pop-up cities, municipalities, DAOs, parallel institutions — all subscribable governance grids. |

---

## Core Unit and Issuance Rule

```
1 TIME = 1 verified hour of human productive capacity

Payment for work is the mint event.
Hard cap: 24 TIME per verified human per day.
```

---

## Reference Applications

| Project | Repo | Status | Role in TIME Protocol |
|---|---|---|---|
| **HumanBond** | [herbstephens/Human-Bond](https://github.com/herbstephens/Human-Bond) | ✅ Live on World Chain + World App | Two-person partnership protocol; 50/50 TIME income split; Partnership Registry API for dating platforms and financial services |
| **VolunteerPROOF** | This repo (`/docs/volunteerproof.md`) | 🔨 In development | Civic contribution credentialing; political campaign volunteer records; soulbound NFTs with early-supporter timing signal |
| **Governance Agent** | This repo (`/docs/governance-agent.md`) | 🔨 In development (Soroban) | Quadratic TIME allocation; jurisdictional map; status-quo signal; Local Multiplier; AI-assisted governance; SCF Build Award Q3 2026 |
| **Utility Concierge** | This repo (`/docs/utility-concierge.md`) | 📋 Specified | Community utility governance; anti-authoritarian infrastructure; Oslo Freedom Forum 2027 debut |

---

## Live Deployments

**World Chain Mainnet — HumanBond V2**

| Contract | Address |
|---|---|
| HumanBond | `0x6494daa4e693F748Eb0a16041ECfCEd51392bB13` |
| TIME Token | `0x261f6d89491cbadff7813303363a514f4b226a82` |
| VowNFT | `0xa1650cc531c2780fb8c006f4b8d314018f7f9ac9` |
| MilestoneNFT | `0x0a2759241d0cb610e3e61db351813ddf8a52f14c` |

**Soroban (Stellar)** — Governance Agent contracts in development; target deployment Q4 2026 pending SCF Build Award.

---

## Canonical Narrative

USD stablecoins tokenize dollars.

TIME tokenizes verified human hours.

HumanBond turns shared time into partnership infrastructure and income recognition.

VolunteerPROOF turns civic hours into portable, verifiable reputation.

Governance Agent turns TIME into political preference — making invisible institutional power visible.

Utility Concierge turns community governance into survival infrastructure that persists regardless of political change.

Network States and jurisdictions turn TIME into census, treasury, citizenship, and legitimacy infrastructure.

---

## Jurisdiction Pilots

| Pilot | Timeline | Scope |
|---|---|---|
| **Valley of the Commons** (Austrian Alps) | Governance Week 2026 | Pop-up city module; Local Multiplier; tiered ID onboarding; Governance Agent testnet |
| **Oslo Freedom Forum** | 2027 | Utility Concierge as anti-authoritarian infrastructure; HRF alignment |
| **Network State** (Balaji framework) | 2027 | Portable governance persona; TIME as sovereign labor standard |

---

## Contract Specification Roadmap

### EVM (World Chain — Live)
- `TIME Token (ERC-20)` ✅
- `HumanBond` ✅
- `VowNFT (ERC-721, soulbound)` ✅
- `MilestoneNFT (ERC-721, soulbound)` ✅

### Soroban (Stellar — In Development)
- `GenesisRegistry` — retroactive birthright calculation
- `BirthrightClock` — 1 TIME/day UBI stream
- `LiquidityLadder` — 1:1 Age Grant unlock
- `AllocationManager` — quadratic governance allocation
- `GovernanceRegistry` — Governance Objects by jurisdiction
- `JurisdictionRegistry` — multi-jurisdiction subscription mesh
- `OrganizationRegistry` — bonded organizations + slashing
- `FraudInvestigation` — quadratic fraud governance
- `GovernanceAgent` — read-only query aggregator
- `ReputationRegistry` — five-dimension reputation score
- `JurisdictionalAccounting` — Local Multiplier calculation

All Soroban contracts to be published under MIT license upon deployment.

---

## Strategic Positioning

TIME Protocol is not competing with Bitcoin. It complements it.

**Bitcoin:** proof-of-work for machines. Converts energy into mathematical scarcity. Store of value and censorship-resistant settlement.

**TIME:** proof-of-work for humans. Converts verified contribution into economic recognition. Labor recognition, governance, reputation, and community coordination layer.

The world needs both.

---

*democracy.earth · June 2026*
