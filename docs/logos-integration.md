# Logos / Waku Integration

## Summary

The Logos integration positions TIME Protocol as the economic module for parallel societies.

Canonical line:

> Logos is building the city. TIME Protocol is its economy.

## Core Module Responsibilities

A Logos TIME module should provide:

- work agreement coordination;
- Waku message listener;
- payment confirmation;
- TIME mint trigger;
- soulbound Work NFT issuance;
- birthright clock;
- decentralized storage for work metadata;
- privacy-preserving balances and records.

## Mint Flow

```text
Worker + payer agree on work
    ↓
Both sign WorkAgreement message
    ↓
Message published to Waku topic
    ↓
Logos TIME module detects agreement
    ↓
Payer sends payment transaction
    ↓
TimeProtocol confirms payment
    ↓
TIME mints to worker
    ↓
Soulbound Work NFT mints as receipt
```

## Waku Topics

Suggested content topics:

```text
/time/1/work-agreements/proto
/time/1/payment-confirmations/proto
/time/1/disputes/proto
/governance/{country}/{region}/{municipality}
/economy/time/marketplace/{region}
/coordination/local/{community-id}
```

## Privacy Model

Recommended default:

| Data | Default State |
|---|---|
| TIME balance | private |
| Work NFT existence | private |
| Work NFT metadata | encrypted / selectively disclosed |
| Payment confirmation | public or ZK-provable |
| World ID nullifier | public enough for anti-Sybil, unlinkable to identity |
| Governance allocation | user-selective: private, aggregated, or public |

## Birthright Clock

The module can include a daily issuance clock:

```text
1 TIME / verified human / day
```

This is the economic floor.

## Work Agreement Schema

A minimal work agreement should include:

```json
{
  "worker": "address or nullifier",
  "payer": "address",
  "hours": "number",
  "jurisdiction": "string",
  "workCategory": "string",
  "paymentAsset": "address or symbol",
  "paymentAmount": "number",
  "startTime": "timestamp",
  "endTime": "timestamp",
  "metadataURI": "encrypted uri",
  "nonce": "string"
}
```

## Integration Goal

TIME should be installable as a module in sovereignty stacks.

A parallel society should be able to add TIME and immediately gain:

- money;
- work accounting;
- birthright UBI;
- proof of contribution;
- governance weight;
- local economic loops.

## Product Narrative

> A parallel society without an economy of work is infrastructure waiting for inhabitants. TIME gives the inhabitants a reason to build and a permanent record that they did.
