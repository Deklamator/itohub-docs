# Структура Проекта

Проект `ito_web` создан на базе Create React App (CRA) и имеет структуру, близкую к методологии Feature-Sliced Design, что обеспечивает хорошую организацию и масштабируемость.

Ниже приведена структура ключевых директорий внутри папки `src/`:




### **Описание ключевых папок:**

* **`app`**: Ядро приложения. Здесь инициализируются глобальные провайдеры и стили.
* **`components`**: "Кубики" для построения интерфейса. Здесь лежат универсальные компоненты, которые используются на разных страницах.
* **`hooks`**: Кастомные хуки React, которые инкапсулируют сложную логику (например, аутентификацию, регулярные запросы к серверу).
* **`pages`**: Каждая папка здесь представляет собой отдельный экран или маршрут в приложении. Страницы собираются из компонентов.
* **`services`**: Сервисный слой, отвечающий за всю коммуникацию с бэкендом.
* **`ton`**: Изолированный модуль для всей логики, связанной с блокчейном TON: формирование транзакций, взаимодействие с контрактами.
* **`types`**: Централизованное место для хранения всех моделей данных (типов TypeScript).
* **`utils`**: Небольшие вспомогательные функции, которые используются в разных частях проекта.