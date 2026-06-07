# VolunteerPROOF

**On-chain civic contribution credentialing. Soulbound. Verifiable. Portable.**

---

## What It Is

VolunteerPROOF enables verified humans to log volunteer hours against bonded community organizations, receiving a **soulbound NFT** — a non-transferable, permanent proof of civic contribution that builds reputation without generating liquid TIME.

It is the civic reputation layer of TIME Protocol: the difference between "I volunteered" (self-reported, unverifiable) and "I have 847 verified volunteer hours across 3 campaigns and 12 organizations" (cryptographic, portable, permanent).

---

## Why It Matters

Volunteer work is one of the most economically invisible forms of human contribution. A person who spends 400 hours canvassing for a candidate six months before a primary election, or 200 hours running a community food bank, has made a substantial economic and social contribution — but in the existing economy, there is no way to prove it. Resumes are self-reported. LinkedIn endorsements are social, not cryptographic. References can be fabricated.

VolunteerPROOF creates the first cryptographically verified, portable, selectively disclosable civic contribution record attached to a human identity — not a wallet, not a platform account, not a resume.

---

## Political Campaigns: The Most Valuable Use Case

Political campaigns are among the most labor-intensive human enterprises, and campaign volunteers are among the most economically unrecognized workers. VolunteerPROOF creates simultaneous value for campaigns and volunteers in ways no existing system provides.

### Value to Campaigns

- **FEC compliance documentation**: verified, tamper-proof record of in-kind volunteer contributions
- **Grassroots credibility**: a campaign that can prove 10,000 verified volunteer hours from 2,000 unique World ID-verified humans has a demonstrably different credibility profile than one that self-reports the same numbers
- **Early adopter ledger**: on-chain record of when supporters committed — provides campaigns with a verifiable momentum signal before it is publicly visible
- **Organizing metrics**: role-specific data (canvassing vs. phone banking vs. field organizing) enables better campaign resource allocation

### Value to Volunteers

Political volunteering is one of the most powerful career signals in existence for roles in government, advocacy, politics, and public affairs — yet it is almost entirely self-reported and unverifiable at the moments that matter most.

VolunteerPROOF creates a permanent, portable, cryptographically verified record of civic contribution attached to the volunteer's World ID identity:

**Timing signal (most important):**
A volunteer who logged 50 hours in the first month of a 12-month campaign has a fundamentally different profile from one who logged 50 hours in the final two weeks. The former is an early believer; the latter is a bandwagon participant. Existing resumes cannot capture this distinction. VolunteerPROOF makes it explicit and immutable.

**Outcome record:**
Post-election, campaign outcome (won / lost) is recorded on-chain by oracle. A verified record of volunteering for a winning campaign two cycles before it won is a powerful career credential that cannot be fabricated.

**Role specificity:**
Field organizing signals different capability than digital outreach or fundraising. Role metadata enables nuanced credential reading by future employers and political organizations.

> *"To whom you volunteer, and when, is career intelligence. VolunteerPROOF makes it verifiable for the first time."*

---

## Soulbound NFT Metadata Schema

Each VolunteerPROOF NFT contains structured metadata:

```json
{
  "type": "VolunteerProofNFT",
  "version": "1.0",
  "world_id_nullifier": "0x...",
  "organization": {
    "registry_id": "0x...",
    "name": "Campaign for [Candidate]",
    "type": "POLITICAL_CAMPAIGN",
    "jurisdiction": "US-PA-07"
  },
  "contribution": {
    "role_type": "FIELD_ORGANIZING",
    "hours_verified": 84,
    "timestamp_start": 1706745600,
    "timestamp_end": 1714521600,
    "election_cycle": "2026-primary",
    "outcome": "PENDING"
  },
  "verification": {
    "volunteer_signature": "0x...",
    "organization_signature": "0x...",
    "verification_timestamp": 1714521601
  },
  "soulbound": true,
  "transferable": false
}
```

### Role Types
```
CANVASSING
PHONE_BANKING
FIELD_ORGANIZING
DIGITAL_OUTREACH
FUNDRAISING
EVENT_ORGANIZING
VOTER_REGISTRATION
LEGAL_OBSERVER
TRANSLATION
MEDICAL_SUPPORT
OTHER
```

### Organization Types
```
POLITICAL_CAMPAIGN
PAC
BALLOT_INITIATIVE
NONPROFIT
MUTUAL_AID
COMMUNITY_ORG
GOVERNMENT
INTERNATIONAL_NGO
OTHER
```

---

## The Organization Registry

Organizations must register and post a financial bond before they can verify volunteer hours. This creates accountability:

### Registration
```solidity
registerOrganization(
    string calldata name,
    OrganizationType orgType,
    bytes32 jurisdictionId,
    uint256 dailyVerificationLimit
) external payable {
    require(msg.value >= MIN_BOND, "Insufficient bond");
    // ...
}
```

**Minimum bond:** Sufficient to deter fraudulent verification. Bond is slashed if organization is found to be verifying fraudulent hours.

### Trust Levels
New organizations start at a low trust level with a daily verification cap. Trust level increases over time with a verified track record:

| Trust level | Daily verification cap | Required track record |
|---|---|---|
| 0 — New | 10 hours/day | None |
| 1 — Established | 100 hours/day | 30 days clean record |
| 2 — Trusted | 1,000 hours/day | 90 days, multi-verifier |
| 3 — Anchor | Unlimited | 1 year, community-verified |

### Slashing
```solidity
slashOrganization(address org, string calldata reason) external onlyGovernance {
    uint256 slashedAmount = organizations[org].bondAmount;
    organizations[org].verified = false;
    organizations[org].bondAmount = 0;
    // Distribute slashed funds to commons treasury + successful investigators
}
```

---

## Fraud Prevention

### Anti-Double-Booking
The UHTC_Calendar contract enforces the 24-hour biological cap. No volunteer can log more hours in a day than physically possible — overlap detection is on-chain.

### Multi-Factor Verification
For high-stakes records (political campaigns, international NGOs), a "double-blind" verification requires both the organization AND an independent peer witness to sign the record.

### FraudInvestigation Integration
If suspicious patterns are detected — an organization verifying impossible hours, statistical anomalies in reporting — any verified human can open a FraudInvestigation. Quadratic-weighted community voting determines outcome. If organization is slashed, bond distributed to whistleblowers.

### Jurisdiction Mapping
All organizations must map to a JurisdictionRegistry entry. Organizations under FraudInvestigation are flagged in the Governance Agent dashboard — users can see which organizations they're supporting are under audit.

---

## Privacy Architecture

The volunteer controls what is disclosed and to whom:

**What is on-chain (public):** NFT existence, organization ID, role type, hours, timestamps, jurisdiction

**What requires World ID disclosure (private by default):**
- Mapping between wallet address and World ID identity
- Personal identity information

**Selective disclosure via ZK proofs:**
A volunteer applying for a political organizing job can prove: *"I have more than 200 verified volunteer hours for a Democratic primary campaign in the 2026 cycle"* — without revealing which campaign, which candidate, or any other dimension of their record.

An employer can verify: *"This applicant has a Civic Reputation score above threshold"* — without seeing the underlying data.

---

## Relationship to Reputation Score

VolunteerPROOF feeds the **Civic Reputation** dimension of the ReputationRegistry:

```typescript
getCivicScore(worldIdNullifier) → {
  score: number,               // 0-1000
  total_hours: number,
  hours_by_org_type: {         // POLITICAL_CAMPAIGN, NONPROFIT, etc.
    [type]: number
  },
  early_supporter_ratio: number, // % of hours logged in first half of campaigns
  outcome_record: {
    won: number,
    lost: number,
    pending: number
  }
}
```

The `early_supporter_ratio` is the single most distinctive metric: it captures the timing dimension that resumes cannot. A high ratio signals conviction and risk tolerance; a low ratio signals late-stage participation. Immutable. Verifiable. Portable.

---

## Sponsored Volunteer TIME

When a community fund or explicit sponsor wants to recognize volunteer work economically, they can mint TIME for verified volunteer hours:

```solidity
sponsorVolunteerTIME(
    address volunteer,
    uint256 hoursVerified,
    address sponsorFund
) external onlyBondedOrg {
    // Transfers sponsorFund tokens → triggers TIME mint for volunteer
    // TIME counts toward 24h/day cap
    // Triggers Liquidity Ladder unlock if volunteer has Age Grant
}
```

This keeps VolunteerPROOF's reputation layer (soulbound NFTs) cleanly separate from the economic layer (liquid TIME) — but allows communities to bridge them when they explicitly choose to.

---

*Part of [The Great Reset](https://github.com/herbstephens/The-Great-Reset) repository*
*democracy.earth · June 2026*
