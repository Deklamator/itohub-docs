# System Overview

The ITOhub platform is a client-server application deeply integrated with the TON blockchain and the Telegram platform.

### Key Components

1.  **Client (Frontend)**: This is a Telegram Mini App written in React. The user interacts exclusively with this interface. The client is responsible for displaying data and sending requests to the backend and the blockchain.

2.  **Backend Server**: The server-side component that manages data not stored on the blockchain. This includes user profiles, offers, deal details, and chats. The backend is also responsible for user authentication via data from Telegram.

3.  **TON Blockchain**: The foundation for all financial operations. All fund transfers occur directly on this network.

4.  **Smart Contract (Escrow)**: A special contract deployed on the TON network. Its main task is to securely hold the buyer's funds during a deal and automatically transfer them to the seller (minus a commission) upon fulfillment of the conditions, or return them to the buyer if the deal is canceled.

### Interaction Principle

A typical scenario (creating a deal) looks like this:
1.  The user in the client (Mini App) accepts the terms of an offer.
2.  The client sends a request to the **backend server** to create a deal record in the database.
3.  For payment, the client uses **TON Connect** to form a transaction and prompts the user to sign it.
4.  The user signs the transaction, and the funds are sent to the **smart contract's** address.
5.  The backend server monitors the smart contract's state, and when the funds arrive, it updates the deal's status in its database, which is then reflected in the client's interface.