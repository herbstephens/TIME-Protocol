# World Chain Deployments

## Status

The Great Reset repo includes a World Chain deployment file listing deployed and verified contracts for the HumanBond / TIME stack.

This file should be maintained as the canonical deployment registry inside TIME Protocol once addresses are confirmed.

## Current Listed Contracts

| Contract | Purpose | Address |
|---|---|---|
| HumanBond | Core Engine | `0x6494daa4e693F748Eb0a16041ECfCEd51392bB13` |
| TIME Token | ERC-20 | `0x261f6d89491cbadff7813303363a514f4b226a82` |
| VowNFT | Soulbound Marriage NFT | `0xa1650cc531c2780fb8c006f4b8d314018f7f9ac9` |
| MilestoneNFT | Anniversary NFTs | `0x0a2759241d0cb610e3e61db351813ddf8a52f14c` |

## Architecture Summary

### HumanBond

Core engine that coordinates:

- World ID verification for both partners;
- relationship proposal and acceptance;
- VowNFT minting;
- divorce flow;
- TIME yield calculation;
- milestone checks.

### TIME Token

ERC-20 token minted under app-specific rules.

For HumanBond, yield is calculated inside the HumanBond contract and minted only when claimed or during divorce settlement.

### VowNFT

Soulbound relationship NFT.

Stores:

- partner addresses;
- marriage timestamp;
- unique relationship ID;
- stateful metadata.

### MilestoneNFT

Anniversary or relationship milestone NFT.

Minted by HumanBond on milestone checks.

## Important Distinction

These deployed contracts are a reference application stack, not necessarily the final canonical TIME Protocol contracts.

Recommended classification:

```text
HumanBond deployment = reference app deployment
Canonical TIME contracts = future protocol-level implementation
```

## Maintenance Checklist

For every deployment, record:

- chain;
- contract name;
- address;
- deployment transaction;
- verifier link;
- source commit hash;
- compiler version;
- constructor args;
- audit status;
- frontend integration status;
- app/protocol classification.

## Frontend Status

The Great Reset deployment note says the frontend demo uses the v1 flow while the technical/protocol review should reference v2 contracts.

Keep this distinction visible until frontend integration catches up.
