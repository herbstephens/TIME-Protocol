# Source Map: The Great Reset Repo

This file maps the newly reviewed Great Reset repository into TIME Protocol.

## Repository

`herbstephens/The-Great-Reset`

Description: files, code, book, pamphlet, and open debate in support of The Great Reset.

## Relevant Files and Folders

| Source | TIME Protocol Integration |
|---|---|
| `README.md` | Reset narrative, wallet thesis, dollar transition framing |
| `time-protocol/` | Earlier protocol implementation and Hardhat structure |
| `land-commons/` | Commons dividend module separate from TIME issuance |
| `volunteerproof/` | Reference app for volunteer hours and impact NFTs |
| `worldchain-deployment.md` | Existing HumanBond / TIME / NFT deployment registry |
| `slides/` | Future deck material |
| `thegreatreset-earth-index.html` | Website narrative source |
| `herb-stephens-speaker.md` | Founder/speaker bio and public narrative material |

## Concepts to Preserve

- TIME as global human time ledger;
- 1 TIME = 1 hour of verified human work;
- World ID as proof-of-humanity layer;
- UniversalCalendar as 24-slot biological constraint;
- WorkReceipt NFTs;
- Land Commons dividends;
- VolunteerPROOF as public-good reference app;
- World Chain deployments;
- reset narrative as civilizational context.

## Concepts to Keep Separate

- TIME token issuance;
- Land Commons dividends;
- book-length narrative;
- political predictions;
- deployed reference app contracts;
- final canonical protocol contracts.

## Integration Decision

Do not merge The Great Reset repo wholesale into TIME Protocol.

Instead, extract:

1. protocol primitives;
2. reference apps;
3. deployment registry;
4. canon context;
5. commons integration;
6. roadmap language.

This keeps TIME Protocol credible as a technical repo while still connected to the broader thesis.
