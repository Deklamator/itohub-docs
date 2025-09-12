
## EN — Security Analysis

### Threat Model

* **Counterparty fraud** — seller not transferring channel rights or not posting ad.
* **Fake channels** — attempts to sell low‑value/fake channels.
* **Replay/duplicate offers** — malicious reuse of deal IDs.
* **Timeout abuse** — buyer or seller intentionally stalls.
* **Smart contract exploits** — incorrect state transitions, re‑entrancy.
* **Sybil attacks** — fake accounts boosting rating/reputation.

### Mitigation Strategies

* **On‑chain escrow** — funds locked in TON until both parties confirm.
* **Timeouts** — automatic cancel if buyer doesn’t fund in time.
* **Unique deal IDs** — enforced by contract hash.
* **DAO/arbiters** — dispute resolution (phase 2).
* **Ratings & reviews** — build user reputation over time.
* **Anti‑fraud AI agents** — anomaly detection in traffic, fake channels, bot activity.