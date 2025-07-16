# Smart Contract Overview

The ITOhub project's smart contract, written in the FunC language, is the core of the platform's secure transaction mechanism.

### Key Role — Centralized Escrow

The contract's primary function is to act as a **centralized escrow service**. This means it temporarily holds the buyer's funds until the terms of the deal are met.

It is important to understand that the contract is not fully decentralized. Key operations, such as dispute resolution, refunds, and commission withdrawal, can only be executed from the **administrator's (moderator's)** wallet. This provides an additional layer of control and the ability to intervene in disputed situations.

### Main Operations (op_codes)

The contract is managed by sending messages with specific operation codes:

* **`op_create_deal (1)`**: Initiates a deal, recording the seller's address, buyer's address, and the amount.
* **`op_fund_deal (5)`**: Funds the deal. The buyer sends funds to the contract.
* **`op_resolve_deal (2)`**: Resolves a dispute. Can only be called by the administrator. Depending on the verdict, funds are sent to the seller (minus a commission) or returned to the buyer.
* **`op_refund_unknown (3)`**: Refunds funds sent to the contract by mistake. Can only be called by the administrator.
* **`op_withdraw_commissions (4)`**: Withdraws the accumulated platform commission. Can only be called by the administrator.