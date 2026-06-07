# Contracts

## Deployed — World Chain Mainnet

See [docs/deployments.md](../docs/deployments.md) for verified addresses.

All HumanBond V2 contracts authored by [@leticarolina](https://github.com/leticarolina).
Source: [herbstephens/Human-Bond/contracts](https://github.com/herbstephens/Human-Bond/tree/main/contracts)

---

## In Specification — Soroban (Stellar)

Target: Q4 2026 · SCF Build Award Q3 2026 · All MIT licensed on deployment

### Core Protocol

**`GenesisRegistry.sol`**
Calculates and mints retroactive birthright TIME (Age × 365) at first verification. Holds as governance-bound until unlocked via LiquidityLadder.
```
calculateAgeGrant(worldIdNullifier) → uint256
claimGrant(worldIdNullifier, identityProof)
getLockedBalance(worldIdNullifier) → uint256
```

**`BirthrightClock.sol`**
Streams 1 TIME/day to all verified humans continuously. Separate accounting from work TIME and Age Grant.
```
streamDaily(worldIdNullifier)
claimAccrued(worldIdNullifier) → uint256
getAccruedBalance(worldIdNullifier) → uint256
```

**`LiquidityLadder.sol`**
Releases governance-bound Age Grant 1:1 as work-backed TIME is earned.
```
updateLiquidity(address user, uint256 newlyEarned)
getTotalUnlocked(address user) → uint256
getRemainingLocked(address user) → uint256
```

**`UHTC_Calendar.sol`**
Enforces 24-hour daily cap; prevents double-booking; manages time slot records.
```
bookSlot(address seller, uint256 startTime, uint256 endTime)
checkAvailability(address seller, uint256 startTime, uint256 endTime) → bool
getDailyUsed(address seller, uint256 date) → uint256
```

### Governance

**`GovernanceRegistry.sol`**
Registry of Governance Objects (laws, budgets, officials, public goods) within each jurisdiction.
```
proposeObject(bytes32 jurisdictionId, ObjectType objType, bytes calldata metadata)
ratifyObject(uint256 proposalId)
getObjectsByJurisdiction(bytes32 jurisdictionId) → GovernanceObject[]
flagObject(uint256 objectId, string calldata reason)
```

**`AllocationManager.sol`**
Quadratic TIME allocation engine. Tracks user allocations, calculates √(tokens) voting power.
```
allocate(uint256 objectId, uint256 amount)
getVotingPower(uint256 objectId, address user) → uint256  // returns √(amount)
getStatusQuo(uint256 objectId) → uint256
unlockAgeGrant(address user, uint256 earnedAmount)
```

**`JurisdictionRegistry.sol`**
Multi-jurisdictional subscription system. Users subscribe to multiple governance grids.
```
subscribe(bytes32 jurisdictionId)
unsubscribe(bytes32 jurisdictionId)
getUserJurisdictions(address user) → bytes32[]
meshJurisdictions(bytes32[] calldata jurisdictionIds) → bytes32 meshId
```

**`GovernanceAgent.sol`** (read-only query aggregator)
Composes data from registry, allocation, and jurisdiction contracts into jurisdiction-specific views.
```
getJurisdictionalView(address user) → JurisdictionalView
getStatusQuoSignal(bytes32 jurisdictionId, uint256 objectId) → uint256
getUserDelta(address user, uint256 objectId) → int256
```

### Civic

**`OrganizationRegistry.sol`**
Registry for bonded organizations with verification privileges. Slashing for fraudulent verification.
```
registerOrganization(string calldata name, OrgType orgType, bytes32 jurisdictionId) external payable
slashOrganization(address org, string calldata reason) external onlyGovernance
getOrgStatus(address org) → OrgStatus
verifyContribution(address volunteer, uint256 hours, RoleType role, bytes32 electionCycle)
```

**`FraudInvestigation.sol`**
Quadratic-weighted community governance over fraud allegations.
```
openInvestigation(address targetOrg, string calldata evidence)
allocateSignal(bytes32 investigationId, uint256 tokens, bool support)
// voting power = √(tokens)
resolve(bytes32 investigationId) external onlyGovernance
unlockTokens(bytes32 investigationId)
// Truth Dividend: slashed bond distributed to successful investigators
```

### Reputation

**`ReputationRegistry.sol`**
Aggregates on-chain activity into five composable reputation dimensions.
```
getWorkScore(bytes32 worldIdNullifier) → (uint256 score, uint256 lastUpdated, uint256 totalHours)
getCivicScore(bytes32 worldIdNullifier) → (uint256 score, CivicBreakdown memory)
getGovernanceScore(bytes32 worldIdNullifier) → (uint256 score, uint256 frequency, bytes32[] memory jurisdictions)
getPartnershipScore(bytes32 worldIdNullifier) → (uint256 score, PartnershipStatus, uint256 durationDays)
getIdentityTier(bytes32 worldIdNullifier) → (uint8 tier, uint256 lastVerified)
getFullProfile(bytes32 worldIdNullifier, bytes calldata disclosureProof) → ReputationProfile
verifyThreshold(bytes32 worldIdNullifier, Dimension dimension, uint256 minimumScore) → bool
```

### Economic Health

**`JurisdictionalAccounting.sol`**
Tracks TIME flow within and across jurisdictions for Local Multiplier calculation.
```
getLocalMultiplier(bytes32 jurisdictionId) → uint256
// multiplier = localTIME / externalTIME
// > 2.0 = strong local economy
// < 1.0 = net extraction

recordFlow(address from, address to, uint256 amount, bytes32 jurisdictionId)
getFlowHistory(bytes32 jurisdictionId, uint256 months) → FlowData[]
```

---

## Open Source Commitment

All Soroban contracts will be published under MIT license on GitHub upon deployment. The TypeScript SDK and REST API wrapping the GovernanceAgent query layer will be published as open standards for any developer to integrate.

---

*Part of [TIME Protocol](https://github.com/herbstephens/TIME-Protocol)*
*democracy.earth · June 2026*
