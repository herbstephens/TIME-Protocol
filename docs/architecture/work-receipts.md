# Work Receipts

## Summary

A Work Receipt is the permanent proof that a verified human hour was contracted, performed, and paid.

In token terms, this is usually a soulbound NFT.

## Why Work Receipts Matter

TIME is fungible.

Work is specific.

A Work Receipt preserves the specific history behind earned TIME without making every TIME token non-fungible.

## Dual-Layer Model

| Layer | Asset | Purpose |
|---|---|---|
| Monetary | TIME ERC-20 | transferable unit of account |
| Historical | Work Receipt NFT | non-transferable proof of contribution |

## Work Receipt Fields

A Work Receipt may include:

```json
{
  "worker": "pseudonymous human identifier",
  "payer": "address or organization",
  "hours": 1,
  "date": "YYYY-MM-DD",
  "timeSlot": "UTC hour or range",
  "workCategory": "string",
  "jurisdiction": "string",
  "paymentAsset": "string",
  "paymentAmount": "number",
  "verificationMethod": "client approval | oracle | organization | dao | self + dispute window",
  "metadataURI": "encrypted or public uri",
  "status": "completed"
}
```

## Privacy Requirements

Work history can be sensitive.

Default model:

- receipt existence may be provable;
- metadata should be encrypted;
- user controls disclosure;
- aggregate proofs are preferred for public dashboards;
- sensitive work categories require stronger privacy.

## Credential Use

Work Receipts can support:

- reputation;
- employment history;
- skill graphs;
- public-good records;
- volunteer credentials;
- jurisdictional economic history;
- network-state GDP-like metrics;
- worker ownership records.

## Payment Rule

A Work Receipt that mints TIME should require payment confirmation.

Canonical phrase:

```text
Payment for work is the mint event.
```

## Volunteer Receipts

VolunteerPROOF receipts may not always have direct payment.

If they mint TIME, the protocol should identify the backing source:

- sponsor payment;
- public-good fund;
- commons pool;
- grant;
- protocol-authorized civic issuance.

## Non-Transferability

Work Receipts should be soulbound.

A person may sell their TIME, but not sell their past.
