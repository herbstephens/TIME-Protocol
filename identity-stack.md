# Identity Stack — Tiered Humanity Stack

**Universal inclusion. Sybil resistance. No human excluded.**

---

## The Design Challenge

TIME Protocol must solve two contradictory requirements simultaneously:
- **Universal inclusion**: no human excluded for lack of government-issued documentation
- **Sybil resistance**: one person cannot claim multiple identities to multiply TIME issuance

The Tiered Humanity Stack resolves this by separating **entry** (anyone can participate) from **capability** (higher verification unlocks more).

---

## The Four Tiers

| Tier | Method | Sybil resistance | Unlocks |
|---|---|---|---|
| **Tier 0 — Peer Vouching** | Three existing verified community members attest identity | Low — community trust, human accountability | Entry: work recording, basic TIME earning, local governance |
| **Tier 1 — Passport NFC** | Cryptographic read of biometric passport chip via NFC | Medium — state-issued ID, cryptographic signature | Work contracts, escrow, volunteer recognition, Age Grant eligibility |
| **Tier 2 — Social Graph** | BrightID or equivalent mesh-network verification | Medium-High — social graph, in-person attestation | Expanded governance weight, cross-jurisdictional governance |
| **Tier 3 — World ID (Apex)** | Iris biometric scan; ZK proof of uniqueness | Very High — biometric uniqueness, ZK privacy | Full governance weight, Age Grant, treasury, partner TIME splits |

---

## Key Design Principles

**Tiers stack, not replace.** A user who begins with peer vouching retains all activity history when they add World ID. Governance weight increases; work history persists.

**Tier 0 requires nothing.** No smartphone. No government ID. No prior crypto experience. Any human being with a community willing to vouch for them can enter the protocol. This is a design requirement, not an accommodation.

**Identity follows the human, not the wallet.** The ReputationRegistry and all protocol state maps to World ID nullifiers — privacy-preserving unique identifiers. Wallet rotation does not reset reputation or identity tier.

**Future-proof.** New verification methods can be added as new tiers without modifying existing user credentials. If World ID is superseded by a better biometric protocol, it becomes Tier 4 — existing Tier 3 users are not disrupted.

---

## The Identity Bridge

The Identity Bridge normalizes heterogeneous identity proofs into a standardized `IdentityClaim` — a signed JSON-LD object:

```json
{
  "@context": "https://timeprotocol.org/identity/v1",
  "@type": "IdentityClaim",
  "subject_id": "did:world:{nullifier}",
  "verification_methods": [
    { "type": "WorldID", "status": "verified", "timestamp": 1717200000 },
    { "type": "PassportNFC", "status": "verified", "timestamp": 1710000000 }
  ],
  "aggregate_trust_score": 100,
  "identity_tier": 3,
  "issued_at": 1717200000
}
```

The `aggregate_trust_score` is a weighted integer (0–100) that determines governance weight across the protocol.

---

## The Village Access Pass

In pop-up city and community contexts (Valley of the Commons, Network States), the Tiered Identity Stack is presented not as "verification levels" but as a **Village Access Pass**:

- **Entry tier (Tier 0)**: Gets you into the village, the Wi-Fi, and the meal plan
- **Governance tier (Tier 1+)**: Unlocks if you choose to participate — entirely optional

Seamless onboarding: arrive, tap your phone or scan your passport, receive your digital key based on identity tier automatically.

---

## World ID Integration

World ID (Tier 3) uses iris biometric scanning and ZK proofs to verify unique humanness without revealing identity:

- **Orb-verified**: iris scan confirms unique human
- **ZK proof**: proves uniqueness without revealing which person
- **Nullifier**: a privacy-preserving unique identifier tied to the specific application action — prevents replay across different actions

HumanBond uses two separate external nullifiers (`propose-bond` and `accept-bond`), ensuring a `propose` proof cannot be replayed as an `accept`.

---

*Part of [TIME Protocol](https://github.com/herbstephens/TIME-Protocol)*
*democracy.earth · June 2026*
