# TIME Protocol Overview

## Definition

TIME Protocol is a decentralized protocol for issuing, tracking, and settling a human-time-denominated digital asset.

The core unit is:

> **1 TIME = 1 verified hour of human productive capacity**

TIME is designed to be minted only when verified human work is contracted, time-reserved, completed or contractually satisfied, and paid for by a real counterparty.

---

## Protocol Objective

TIME Protocol aims to create a global, programmable, non-sovereign unit of account for human work.

The protocol is designed to answer four questions:

1. **Who performed the work?**
2. **Was the person a unique verified human?**
3. **Was the time real and not double-booked?**
4. **Was payment received for the work?**

When those conditions are satisfied, TIME can be minted as a work-backed digital asset.

---

## Core Components

### 1. Proof of Humanity

The protocol requires a mechanism to verify that each participant is a unique human.

This prevents Sybil attacks, where one person creates many identities to claim more time than biologically possible.

### 2. Proof of Time

The protocol tracks human time allocation.

A verified human should not be able to sell, pledge, or mint the same hour twice.

### 3. Proof of Work

The protocol records that contracted work was performed or contractually satisfied.

This may be established through client approval, milestone completion, oracle input, DAO vote, signed attestations, geolocation, device proofs, or other verification mechanisms depending on the type of work.

### 4. Proof of Payment

TIME should be minted only when real payment is received.

This is the key distinction between theoretical labor credit and payment-backed work settlement.

### 5. Minting Logic

TIME is minted after the protocol verifies:

- human identity;
- time reservation;
- work agreement;
- completion or satisfaction;
- payment receipt.

### 6. Escrow

Payments may be routed through escrow contracts that hold funds until work is completed or otherwise resolved.

### 7. Metadata and Reputation

Each verified work event may generate metadata useful for:

- worker reputation;
- credentials;
- employment history;
- skill graphs;
- tax records;
- dispute resolution;
- future work matching.

---

## Example Workflow

```text
1. Worker verifies humanity.
2. Client creates work contract.
3. Worker accepts contract and reserves time.
4. Payment is placed in escrow.
5. Work is performed.
6. Client approves or oracle verifies completion.
7. Escrow releases payment.
8. Protocol mints TIME corresponding to verified paid hours.
9. Work record is stored as credential/reputation metadata.
```

---

## Supply Constraint

TIME supply is limited by biological and economic constraints.

The theoretical upper bound is:

```text
verified humans × 24 hours per day
```

The practical minted supply is lower:

```text
verified humans × verified hours sold × actual paid demand
```

This makes TIME resistant to arbitrary monetary inflation.

---

## Why TIME Is Not Just a Labor Token

TIME is not merely a claim that labor occurred.

TIME is a tokenized representation of **paid, verified human work capacity**.

That distinction matters because unpaid or self-reported labor does not establish market-clearing value. Payment by a real counterparty creates the economic backing.

---

## Potential Use Cases

### Payroll

Employers can pay workers in TIME or use TIME as a unit for payroll accounting.

### Freelancing

Freelancers can issue work contracts denominated in verified hours.

### UBI

A protocol-level UBI stream can distribute a baseline allocation of TIME-linked value to verified humans.

### Volunteer Work

Nonprofits, DAOs, and governments can recognize and reward verified service hours.

### Taxation

Jurisdictions can calculate taxes based on verified work and payment flows.

### Reputation

Workers can build portable work-history credentials based on verified paid time.

### AI-Era Labor Markets

TIME can distinguish verified human contribution from synthetic or automated output.

---

## Design Principle

TIME should not attempt to become a synthetic dollar.

The protocol should instead preserve the integrity of its native unit:

> **the verified human hour.**
