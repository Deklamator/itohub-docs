# Smart Contract Overview

The ITOhub project's smart contract, written in the FunC language, is the core of the platform's secure transaction mechanism.

### Key Role — Centralized Escrow

The contract's primary function is to act as a **centralized escrow service**. This means it temporarily holds the buyer's funds until the terms of the deal are met.

It is important to understand that the contract is not fully decentralized. Key operations, such as dispute resolution, refunds, and commission withdrawal, can only be executed from the **administrator's (moderator's)** wallet. This provides an additional layer of control and the ability to intervene in disputed situations.

