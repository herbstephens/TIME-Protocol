# Contracts Roadmap

This directory is reserved for canonical TIME Protocol contracts.

The parent repository should eventually define clean reference implementations, while application repositories may maintain their own specialized contracts.

## Proposed Contract Modules

```text
contracts/
├── interfaces/
│   ├── IProofOfHumanity.sol
│   ├── ITimeToken.sol
│   ├── IWorkNFT.sol
│   └── IGovernanceRegistry.sol
├── core/
│   ├── TimeToken.sol
│   ├── BirthrightClock.sol
│   ├── WorkAgreement.sol
│   ├── WorkNFT.sol
│   └── TimeProtocol.sol
├── governance/
│   ├── GovernanceRegistry.sol
│   ├── GovernanceAllocator.sol
│   ├── QuadraticVoting.sol
│   └── CommonsVault.sol
├── jurisdiction/
│   ├── JurisdictionRegistry.sol
│   ├── Clearinghouse.sol
│   └── LandCommonsOracle.sol
└── test/
    ├── TimeToken.t.sol
    ├── DailyCapInvariant.t.sol
    ├── WorkMinting.t.sol
    └── GovernanceAllocation.t.sol
```

## Core Invariants

1. One verified human cannot mint more than 24 new TIME per day.
2. Birthright issuance requires proof of humanity.
3. Work issuance requires payment confirmation.
4. Work NFTs are soulbound.
5. Governance allocation must be attributable to a verified human or privacy-preserving nullifier.
6. Quadratic vote weight should be computed from allocated TIME.
7. Human-to-human transactions may be fee-free; corporate/capital transactions may route fees to commons vaults.

## Reference Implementations to Consolidate

The following existing repositories contain contract or architecture material that should be reviewed before writing canonical contracts:

- `Governance-Agent`
- `OpenClaw-Governance-Agent-on-NEAR`
- `Human-Bond`
- `Marriage-DAO`
- `logos-time-module`
- `The-Network-State`
- `Liberland`

## Recommended Next Step

Start with interfaces and invariant tests before importing app-specific code.
