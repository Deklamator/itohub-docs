# Data Model

This page describes the main entities (data models) that are used on the application's backend to store information.

### `Creator` (User)
Represents a user of the platform.

* **Fields**: `{ id, telegram_id, username, rating, avatar_url }`

### `Channel`
Represents a Telegram channel that can be sold or where an ad can be placed.

* **Fields**: `{ id, telegram_id, type, username, subscriber_count, avg_post_reach, is_verified, photo_url }`

### `Offer`
An offer to sell an asset (a channel or an ad).

* **Fields**: `{ id, creator, channel, offer_type, price, currency_type, code, title, description, ... }`

### `Deal`
An agreed-upon and confirmed transaction between a buyer and a seller.

* **Fields**: `{ id, offer_id, buyer_id, seller_id, amount, status, created_at, buyer, seller, channel, ... }`

### `OfferRequest`
A request from a buyer to accept the terms of an offer.

* **Fields**: `{ id, offer_id, buyer_id, status, ... }`

### `RewardTask`
Describes a task for which a user receives points upon completion.

* **Fields**: `{ id, title, description, points_reward, ... }`

### `ChatMessage`
A message within the chat of a specific deal.

* **Fields**: `{ id, content, sender_id, timestamp, is_read, ... }`