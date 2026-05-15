# VolunteerPROOF

## Summary

VolunteerPROOF is a TIME Protocol reference application for public-good contribution.

It lets verified humans log volunteer hours, mint proof NFTs, and eventually earn TIME for verified contribution.

## Role in TIME Protocol

VolunteerPROOF expands TIME beyond paid market labor.

It asks:

> How should public-good labor, volunteer service, and civic contribution be verified and recognized?

## Core Flow

```text
1. Verify humanity through World ID.
2. Log volunteer hours.
3. Attach organization, description, category, and time.
4. Organization or verifier confirms contribution.
5. Mint soulbound VolunteerProof NFT.
6. Optionally claim TIME or reputation according to protocol rules.
```

## Key Objects

### Volunteer Entry

A record of claimed service.

Fields may include:

- human nullifier;
- organization;
- hours;
- date;
- description;
- category;
- jurisdiction;
- verifier;
- status.

### VolunteerProof NFT

A non-transferable proof of verified service.

Metadata may include:

- hours;
- organization;
- impact category;
- verification status;
- cumulative impact;
- optional encrypted details.

### TIME Yield

Volunteer hours may earn TIME if the protocol or sponsoring organization funds or authorizes the issuance.

Important distinction:

- paid work TIME is backed by payment;
- volunteer TIME may be backed by public-good allocation, grants, commons pools, or protocol rules.

## Integration Options

### Conservative

VolunteerPROOF mints NFTs only.

No TIME is minted until a funder pays for the hours.

### Sponsored

A nonprofit, government, DAO, or commons pool funds volunteer hours.

Payment triggers TIME minting.

### Protocol Recognition

A limited category of volunteer TIME is authorized as public-good issuance.

This requires stricter governance.

## Recommended Initial Rule

Use the sponsored model first:

```text
Volunteer TIME requires organization verification and sponsor funding.
```

This preserves the core principle:

```text
Payment for work is the mint event.
```

## Why It Matters

VolunteerPROOF lets TIME Protocol serve:

- nonprofits;
- public goods;
- civic service;
- disaster response;
- mutual aid;
- community projects;
- youth service;
- impact credentials.

## Product Narrative

> Verify your humanity. Log your impact. Mint your proof.
