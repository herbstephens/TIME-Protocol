# TIME Protocol

**The human-anchoring layer for an AI-dominant economy.**

> *1 TIME = 1 verified hour of human existence*
> *The dollar is a political unit. The hour is a biological unit.*
> *TIME Protocol is the first monetary protocol built on the latter.*

[![World Chain](https://img.shields.io/badge/World%20Chain-Mainnet-1A1D3A?style=flat-square)](https://worldscan.org)
[![HumanBond](https://img.shields.io/badge/HumanBond-Live%20in%20World%20App-6B4FBB?style=flat-square)](https://github.com/herbstephens/Human-Bond)
[![SCF](https://img.shields.io/badge/SCF%20Build%20Award-Q3%202026-1B4F8B?style=flat-square)](./docs/scf-build-award.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-gray?style=flat-square)](./LICENSE)

---

## What Is TIME Protocol?

TIME Protocol is a monetary primitive built on biological scarcity. Every verified human on earth receives exactly 24 TIME per day — no more, no less. That ceiling is not a governance parameter. It is a physical law.

TIME is minted only when real work is contracted, verified, and paid for — or streamed as a daily birthright to every verified human. It is the first **labor-backed stable asset**: collateralized by verified human productivity and real payments, denominated in the one resource every human holds in precisely equal daily supply.

**Bitcoin converts energy into scarcity. TIME converts verified human contribution into money.**

---

## Core Thesis

**USD stablecoins are stable against a currency. TIME is stable against civilization's primary scarce asset: human life-hours.**

Dollar-pegged stablecoins stabilize one exchange rate: token-to-dollar. They do not stabilize purchasing power, labor value, local-currency value, or human economic opportunity. The honest name for them is **dollarcoins** — tokenized offshore dollar liquidity.

TIME Protocol offers a different reference unit: the verified human hour. Its scarcity is biological, not mathematical, geological, or political:

| Scarcity type | Example | Source |
|---|---|---|
| Mathematical | Bitcoin (21M cap) | Algorithm |
| Geological | Gold | Earth deposits |
| Political | Fiat currency | Central bank |
| **Biological** | **TIME (24h/day/human)** | **Physical law** |

No central bank can print more hours. No government can extend the length of a day. No amount of capital can purchase more human time.

---

## The Four Issuance Primitives

| Primitive | Mechanism | Daily limit |
|---|---|---|
| **Retroactive Birthright** | Age × 365 TIME at first verification, governance-bound | One-time genesis grant |
| **Daily UBI** | 1 TIME/day streamed continuously to all verified humans | 1 TIME |
| **Work TIME** | Minted only when real payment is received for verified work | Up to 23 TIME |
| **Volunteer TIME** | Minted when a bonded organization sponsors hours | Within 24 TIME total |

**Hard cap: 24 TIME per verified human per day — enforced on-chain, non-overridable by any governance action.**

### The Retroactive Birthright

```
retroactive_birthright_TIME = age_in_years × 365

e.g. 40 years × 365 = 14,600 TIME at first verification
```

Every verified human enters the protocol with capital proportional to their lived experience. The grant is governance-bound at verification and unlocks 1:1 as work-backed TIME is earned (the **Liquidity Ladder**). Anti-speculation by design.

**The protocol does not create human time. It recognizes it.**

---

## Live Deployments

**HumanBond V2 — World Chain Mainnet**

| Contract | Address |
|---|---|
| HumanBond | `0x6494daa4e693F748Eb0a16041ECfCEd51392bB13` |
| TIME Token (ERC-20) | `0x261f6d89491cbadff7813303363a514f4b226a82` |
| VowNFT (ERC-721) | `0xa1650cc531c2780fb8c006f4b8d314018f7f9ac9` |
| MilestoneNFT (ERC-721) | `0x0a2759241d0cb610e3e61db351813ddf8a52f14c` |

**HumanBond Mini App** — live in World App store · search `HumanBond`

**Governance Agent** — in development on Soroban (Stellar) · SCF Build Award Q3 2026

---

## Reference Applications

| App | Status | Description |
|---|---|---|
| [**HumanBond**](https://github.com/herbstephens/Human-Bond) | ✅ Live | Two-person partnership protocol. 50/50 TIME income split. Partnership Registry API for dating platforms. |
| **VolunteerPROOF** | 🔨 In development | Civic contribution credentialing. Political campaign volunteer records. Soulbound NFTs. |
| **Governance Agent** | 🔨 In development (Soroban) | Quadratic allocation, jurisdictional map, Local Multiplier, AI-assisted governance. |
| **Utility Concierge** | 📋 Specified | Community utility governance. Anti-authoritarian infrastructure. Oslo Freedom Forum 2027. |

---

## Repository Structure

```
TIME-Protocol/
├── README.md                              ← You are here
├── PROJECT-MAP.md                         ← Protocol stack and reference app map
├── WHITEPAPER.md                          ← Full technical and economic whitepaper
├── docs/
│   ├── tokenomics.md                      ← Issuance, scarcity, monetary design
│   ├── identity-stack.md                  ← Tiered Humanity Stack (Tier 0–3)
│   ├── reputation-score.md                ← Five-dimension reputation architecture
│   ├── governance-agent.md                ← Governance Agent specification
│   ├── utility-concierge.md               ← Utility Concierge + persistence mechanisms
│   ├── humanbond.md                       ← HumanBond + Partnership Registry
│   ├── volunteerproof.md                  ← VolunteerPROOF + political campaigns
│   ├── liquidity-ladder.md                ← Age Grant unlock mechanics
│   ├── local-multiplier.md                ← Community economic health metric
│   ├── stablecoin-thesis.md               ← Dollar stablecoin critique
│   ├── monetary-principles.md             ← Core monetary design principles
│   ├── canon.md                           ← Book trilogy intellectual foundation
│   ├── deployments.md                     ← Live contract addresses
│   └── scf-build-award.md                 ← SCF Build Award application summary
├── contracts/
│   └── README.md                          ← Contract specifications
└── LICENSE
```

---

## Upcoming Milestones

| Event | Date | Deliverable |
|---|---|---|
| **ETHGlobal Lisbon** | July 24–26, 2026 | HumanBond live demo; Age Grant UI; Governance Agent UI; hackathon prizes |
| **SCF Build Award** | Q3 2026 | Governance Agent on Soroban; $150K award |
| **Valley of the Commons** | Governance Week 2026 | Pop-up city pilot; Local Multiplier live; tiered ID |
| **Oslo Freedom Forum** | 2027 | Utility Concierge debut as anti-authoritarian infrastructure |

---

## The Book Trilogy

TIME Protocol is the technical implementation of a three-book intellectual project by Herb Stephens:

| Book | Diagnosis | Protocol response |
|---|---|---|
| [**The Lie Factory**](https://www.amazon.com/Lie-Factory-Orgasms-Childhood-Intimacy/dp/B0GM81PB3T/) *(live on Amazon)* | Information weaponized to manufacture consent | Governance Agent as anti-lie infrastructure |
| **The Lie of Investing** *(manuscript complete)* | Capital extraction masquerading as wealth creation | Work-backed TIME, Local Multiplier, Age Grant |
| **The Great Reset** *(manuscript complete)* | Civilizational transition is necessary and possible | TIME Protocol as coordination layer; 2034 Schelling point |

---

## Team

**Herb Stephens** — Co-Founder, Democracy Earth Foundation (with Santiago Siri). Creator of Democracy OS and Proof of Humanity. Author of The Lie Factory. herb@democracy.earth

**Franco** — Frontend / MiniKit. Lead developer, HumanBond Mini App.

**Leticia** — Smart contracts. HumanBond V2 deployed and verified on World Chain Mainnet.

---

## License

MIT — all code open source. All Soroban contracts published under MIT upon deployment.

---

*democracy.earth · github.com/herbstephens/TIME-Protocol · June 2026*
