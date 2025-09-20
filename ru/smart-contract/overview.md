# Smart Contract Overview / Обзор смарт-контракта

> **Target files:**
>
> • `en/smart-contract/overview.md`
>
> • `ru/smart-contract/overview.md`

---

## EN — Smart Contract Overview

### 1. Purpose

The ITOhub smart contract ensures **escrow-protected P2P deals** on the TON blockchain. Funds are locked until the seller fulfills obligations (channel transfer, ad placement, bot rental).

### 2. State Machine

```mermaid
stateDiagram-v2
    [*] --> PendingPayment
    PendingPayment --> Funded : op_fund_deal
    PendingPayment --> Cancelled : timeout / op_cancel_deal
    Funded --> Resolved : op_resolve_deal
    Funded --> Disputed : op_dispute
    Disputed --> Resolved : DAO/arbiters
    Disputed --> Cancelled : DAO/arbiters
    Resolved --> [*]
    Cancelled --> [*]
```

### 3. Transactions & Ops

| Code              | Operation   | Actor            | Effect                          |
| ----------------- | ----------- | ---------------- | ------------------------------- |
| `op_create_deal`  | Create deal | Seller/Buyer     | Init escrow contract            |
| `op_fund_deal`    | Fund deal   | Buyer            | Lock TON funds                  |
| `op_resolve_deal` | Resolve     | Seller+Buyer     | Release funds to seller –3% fee |
| `op_cancel_deal`  | Cancel      | Timeout / mutual | Refund buyer                    |
| `op_dispute`      | Dispute     | Buyer/Seller     | Escalate to DAO/arbiters        |

### 4. World-State (σ)

* σ : id → { User, Channel, Deal, Passport, Offer }
* **On-chain:** escrow status, wallets, Token Passport root.
* **Off-chain:** metrics, extended history (Postgres, Redis, IPFS).

### 5. Fees & Gas

* Protocol fee: **3%** flat.
* Gas: ≈ **0.02 TON** per tx.
* Future: referrer share, treasury split, burn.

### 6. Security Notes

* Immutable contract on TON.
* Timeout prevents deadlocks.
* DAO/arbiters for disputes.
* External audit + fuzz-tests recommended.

---

## RU — Обзор смарт-контракта

### 1. Назначение

Смарт-контракт ITOhub обеспечивает **P2P-сделки с эскроу** в блокчейне TON. Средства блокируются до тех пор, пока продавец не выполнит обязательства (передача канала, размещение рекламы, аренда бота).

### 2. Машина состояний

```mermaid
stateDiagram-v2
    [*] --> ОжиданиеОплаты
    ОжиданиеОплаты --> Фандировано : op_fund_deal
    ОжиданиеОплаты --> Отменено : таймаут / op_cancel_deal
    Фандировано --> Завершено : op_resolve_deal
    Фандировано --> Спор : op_dispute
    Спор --> Завершено : DAO/арбитры
    Спор --> Отменено : DAO/арбитры
    Завершено --> [*]
    Отменено --> [*]
```

### 3. Транзакции и операции

| Код               | Операция        | Участник            | Эффект                        |
| ----------------- | --------------- | ------------------- | ----------------------------- |
| `op_create_deal`  | Создание сделки | Продавец/Покупатель | Инициализация эскроу          |
| `op_fund_deal`    | Фандинг сделки  | Покупатель          | Блокировка TON                |
| `op_resolve_deal` | Завершение      | Продавец+Покупатель | Выплата продавцу –3% комиссии |
| `op_cancel_deal`  | Отмена          | Таймаут / согласие  | Возврат средств покупателю    |
| `op_dispute`      | Спор            | Продавец/Покупатель | Эскалация в DAO/арбитраж      |

### 4. Мировое состояние (σ)

* σ : id → { User, Channel, Deal, Passport, Offer }
* **On-chain:** статус эскроу, кошельки, корень Token Passport.
* **Off-chain:** метрики, расширенная история (Postgres, Redis, IPFS).

### 5. Комиссии и газ

* Комиссия протокола: **3%**.
* Gas: ≈ **0.02 TON** за транзакцию.
* В планах: реферальные бонусы, распределение в казну, сжигание.
