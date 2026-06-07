# Utility Concierge — Architecture Specification

> *"Authoritarianism requires leverage. Utilities are leverage. Remove the leverage and the playbook fails."*

---

## What It Is

The Utility Concierge is a background governance system that makes essential community services — water, energy, waste management, local economy, public safety — persist regardless of political change.

It is not infrastructure. It governs infrastructure. The physical pipes, wires, and treatment plants remain exactly where they are, owned and operated by whoever currently operates them. What the Concierge provides is a **governance and accountability layer** on top of that infrastructure: transparent, tamper-resistant, and immune to capture by any single political actor.

---

## Answering the Critics

### "This Is Privatization"

**Wrong.** The Concierge does not own or operate utilities. It makes the governance of utilities resistant to capture. Making governance resistant to political capture is the deepest form of democratic protection — not its negation.

### "This Is Anarchist Infrastructure"

**Wrong.** The Concierge is designed to complement functioning government, not replace it. In stable democracies, it adds transparency and accountability. In authoritarian environments, it ensures essential services continue when governments deliberately fail to provide them or weaponize them.

---

## Core Design Principle: Continuity as Default

**In the absence of any governance action, utilities continue at their last verified operational parameters.**

Silence means continuation, not cessation. This is the precise inverse of how political capture works: when a regime wants to weaponize a utility, they must take an affirmative action. The Concierge makes affirmative actions slow, transparent, and subject to citizen ratification. It does not make them impossible — but it makes them impossible to do quickly, quietly, or unilaterally.

---

## The Five Persistence Mechanisms

### 1. Constitutional Immutables
Core utility parameters encoded as immutable contract variables. No governance vote can change them. Only a verified supermajority of citizens with a mandatory 90-day public notice period can trigger an amendment process.

**Examples:**
- Minimum WHO water quality standards
- Maximum consecutive outage duration
- Maximum price as percentage of median income
- Minimum delivery pressure at access point

### 2. Mandatory Time-Lock
Any governance decision affecting a utility must wait a mandatory delay before execution. Enforced by the contract — no administrative override.

| Change type | Time-lock |
|---|---|
| Operational | 30 days |
| Structural | 90 days |
| Constitutional | 180 days |

**Prevents:** Rapid weaponization by newly installed authorities; emergency powers exploitation; cover-of-night policy changes.

### 3. Citizen Ratification
Changes proposed by any authority — elected, appointed, or administrative — require ratification by a threshold of verified citizens before execution.

| Change type | Ratification threshold |
|---|---|
| Operational | 15% of verified residents |
| Structural | 30% of verified residents |
| Constitutional | Supermajority (community-set, typically 60%+) |

**Prevents:** Unilateral action regardless of formal authority; rubber-stamp approval by captured legislative bodies.

### 4. Distributed Multi-Signature
No single key, address, or individual can alter utility parameters. All operational changes require M-of-N cryptographic signatures from a geographically and socially distributed set of Community Stewards.

**Steward properties:**
- Fixed, non-renewable terms (prevents entrenchment)
- Geographically distributed (represents full jurisdiction)
- Financially bonded (TIME bond slashed on malfeasance)
- Fully transparent decision records (on-chain)
- Subject to recall by supermajority at any time

### 5. Automatic Continuity
No ongoing input required to maintain service standards. The contract continues executing at last verified parameters until a ratified, time-locked, multi-signed governance action changes them.

---

## The Three-Layer Architecture

| Layer | What it covers | Who governs it | How change happens |
|---|---|---|---|
| **Physical Infrastructure** | Pipes, wires, plants, facilities | Existing operators (unchanged) | Not in scope — physical assets stay as-is |
| **Operational Governance** | Budgets, standards, contractor selection, monitoring | Community-verified citizens via TIME-weighted quadratic voting | Proposal → Time-lock → Steward review → Citizen ratification → Auto-execution |
| **Emergency Response** | Anomaly detection, crisis budget activation | Automated triggers + Steward ratification | System detects → Stewards activate → Community ratifies within 72h → Auto-expiry without renewal vote |

---

## Utility Categories

### Water & Sanitation
**Constitutional immutables:** Minimum WHO water quality standards; maximum price as % of median income; maximum consecutive outage hours; minimum pressure at delivery point.

**Anomaly triggers:** Quality below standard; pressure below minimum; outage exceeding threshold; contractor non-performance.

### Electricity & Energy
**Constitutional immutables:** Maximum outage duration; minimum reliability percentage; maximum price per kWh relative to median income; minimum reserve capacity.

**Anomaly triggers:** Outage duration exceeded; reliability below threshold; price spike above cap; reserve below minimum.

### Waste Management
**Constitutional immutables:** Minimum collection frequency; maximum landfill proximity to residential areas; minimum recycling diversion rate.

**Anomaly triggers:** Collection below standard; treatment failure; illegal dumping density threshold.

### Local Economic Infrastructure
**Constitutional immutables:** Minimum Local Multiplier score; maximum market concentration by any single supplier; minimum commons fund contribution rate.

**Anomaly triggers:** Multiplier below threshold; monopoly concentration detected; supply chain failure.

### Public Safety Infrastructure
**Constitutional immutables:** Minimum lighting coverage; emergency communication uptime; alert system test frequency.

**Anomaly triggers:** Lighting failure coverage; communication network down; alert system failure.

---

## The Five Deployment Stages

Communities adopt stages based on their context and trust level. Stable democracies typically need only Stages 1-2. Authoritarian environments may need Stages 4-5.

| Stage | Name | Description | Governance relationship |
|---|---|---|---|
| **1** | Transparency Layer | Monitor and report on existing utility performance. Read-only. | Fully complementary — no control. |
| **2** | Accountability Layer | Performance data triggers public reports and Steward notifications. | Advisory — informs residents; existing authorities retain all decision power. |
| **3** | Budget Layer | Community controls a portion of utility budget allocation. | Shared — existing operators continue; community governs defined budget portion. |
| **4** | Governance Layer | Full Concierge deployment. Community Stewards govern operational decisions. Constitutional Immutables active. | Primary — community governance layer is live. Existing operators become contractors accountable to the Concierge. |
| **5** | Resilience Layer | Full deployment with redundant physical infrastructure backup. | Self-sufficient — community can maintain essential services independently for defined duration. |

**Most communities:** Stages 1-2 represent significant improvement over current utility governance — simply making performance data public changes the incentive structure for administrators and contractors.

**Oslo Freedom Forum audience (authoritarian environments):** Need Stages 4-5. The Valley of the Commons pilot demonstrates Stage 3 with elements of Stage 4 during Governance Week.

---

## What Residents Experience

**For the 90%:** The Concierge is invisible. Background process. Weekly summary: service performance metrics, budget utilization, Local Multiplier score. Nothing required.

**Three states:**
- 🟢 **Green** — Everything normal. Weekly summary only.
- 🟡 **Yellow** — Anomaly detected or governance decision approaching threshold. Notification with context and options.
- 🔴 **Red** — Critical incident. Full data, proposed responses, call to action. Rare by design.

**What residents never experience with the Concierge active:**
- A politician announcing water rates are tripling effective immediately
- A new administration quietly redirecting infrastructure budgets to favored contractors
- A regime cutting power to a neighborhood that voted the wrong way

These actions require the same ratification, time-lock, and multi-signature process as any other governance change — and Constitutional Immutables make some of them impossible regardless of who holds power.

---

## The Human Rights Foundation Alignment

The Utility Concierge is the answer to what activists, dissidents, and aid workers consistently report at forums like the Oslo Freedom Forum:

> People under authoritarian control are not primarily asking for ideological alternatives. They want clean water. They want the garbage collected. They want reliable electricity. They want to know their children will be safe.

Bitcoin addresses the monetary capture layer of authoritarian control. The Utility Concierge addresses the physical infrastructure layer. A community with monetary sovereignty but no clean water is still controlled by whoever controls the water.

**The argument is not technical. It is human.**

Every utility failure in every authoritarian context follows the same script: essential services are degraded, residents become desperate, desperation becomes leverage, leverage becomes compliance. The Utility Concierge interrupts this script at the leverage step — not by fighting the regime, not by replacing the government, but by making essential services persist regardless of what the regime decides.

This is survival infrastructure.

---

## Oslo Freedom Forum 2027 Target

The Utility Concierge is the centerpiece of the TIME Protocol's Oslo Freedom Forum 2027 presentation, being coordinated with Alex Gladstein and the Human Rights Foundation.

**Framing:** Not a blockchain project. Not a governance experiment. The missing infrastructure layer between digital sovereignty (Bitcoin) and physical survival.

**See also:** [`/docs/canon/the-lie-factory.md`](../canon/the-lie-factory.md) for the information-capture diagnosis that the Governance Agent addresses; and the whitepaper Section 9 for the full Utility Concierge architecture.

---

*Part of [The Great Reset](https://github.com/herbstephens/The-Great-Reset) repository*
*democracy.earth · June 2026*
