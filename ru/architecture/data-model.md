# Модель Данных

На этой странице описаны основные сущности (модели данных), которые используются на бэкенде приложения для хранения информации.

### `Creator` (Пользователь)
Представляет пользователя платформы.

* **Поля**: `{ id, telegram_id, username, rating, avatar_url }`

### `Channel` (Канал)
Представляет Telegram-канал, который может быть продан или в котором может быть размещена реклама.

* **Поля**: `{ id, telegram_id, type, username, subscriber_count, avg_post_reach, is_verified, photo_url }`

### `Offer` (Оффер)
Предложение о продаже актива (канала или рекламы).

* **Поля**: `{ id, creator, channel, offer_type, price, currency_type, code, title, description, ... }`

### `Deal` (Сделка)
Согласованная и подтвержденная операция между покупателем и продавцом.

* **Поля**: `{ id, offer_id, buyer_id, seller_id, amount, status, created_at, buyer, seller, channel, ... }`

### `OfferRequest` (Запрос на оффер)
Заявка от покупателя на принятие условий оффера.

* **Поля**: `{ id, offer_id, buyer_id, status, ... }`

### `RewardTask` (Задание для вознаграждения)
Описывает задание, за выполнение которого пользователь получает очки.

* **Поля**: `{ id, title, description, points_reward, ... }`

### `ChatMessage` (Сообщение в чате)
Сообщение в чате конкретной сделки.

* **Поля**: `{ id, content, sender_id, timestamp, is_read, ... }`