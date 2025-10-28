# API Testing Checklist: Flowwow.com

**Назначение:** Проверка API endpoints и интеграций  
**Инструменты:** Postman, Chrome DevTools  
**Базовый URL:** `https://api.flowwow.com` 
**Формат данных:** JSON

---

##  АУТЕНТИФИКАЦИЯ
### Регистрация и вход
- [ ] **POST /api/v1/auth/register** - регистрация по номеру телефона
  - Request: `{“phone”: “+79991234567”}`
  - Response: `{“success”: true, “message”: “SMS sent”}`

- [ ] **POST /api/v1/auth/verify** - подтверждение SMS кода
  - Request: `{“phone”: “+79991234567”, “code”: “123456”}`
  - Response: `{“success”: true, “token”: “jwt_token”}`

- [ ] **POST /api/v1/auth/login** - вход по номеру телефона
  - Request: `{“phone”: “+79991234567”}`
  - Response: `{“success”: true, “message”: “SMS sent”}`

### Работа с токеном
- [ ] **GET /api/v1/user/profile** - получение профиля с валидным токеном
- [ ] **GET /api/v1/user/profile** - запрос без токена (401 Unauthorized)
- [ ] **GET /api/v1/user/profile** - запрос с невалидным токеном (401)

## КАТАЛОГ И ПОИСК
### Товары и категории
- [ ] **GET /api/v1/categories** - получение списка категорий
  - Response: `[{“id”: 1, “name”: “Цветы”, “slug”: “flowers”}]`

- [ ] **GET /api/v1/products** - получение товаров (с пагинацией)
  - Query params: `?page=1&limit=20`
  - Response содержит: `products[], total, current_page`

- [ ] **GET /api/v1/products/{id}** - получение конкретного товара
  - Response: полная информация о товаре + изображения

### Поиск и фильтрация
- [ ] **GET /api/v1/search** - поиск товаров
  - Query params: `?q=розы&city=москва`
  - Response: релевантные товары + фильтры

- [ ] **GET /api/v1/search/suggest** - поисковые подсказки
  - Query params: `?q=роз`
  - Response: `[“розы”, “розы белые”, “розы красные”]`

## КОРЗИНА И ЗАКАЗЫ
### Управление корзиной
- [ ] **POST /api/v1/cart/add** - добавление товара в корзину
  - Request: `{“product_id”: 123, “quantity”: 1}`
  - Response: обновленная корзина

- [ ] **GET /api/v1/cart** - получение содержимого корзины
- [ ] **PUT /api/v1/cart/update** - изменение количества
- [ ] **DELETE /api/v1/cart/remove** - удаление товара

### Оформление заказа
- [ ] **POST /api/v1/orders** - создание заказа
  - Request: данные доставки, товары, способ оплаты
  - Response: `{“order_id”: 456, “status”: “created”}`

- [ ] **GET /api/v1/orders** - история заказов
- [ ] **GET /api/v1/orders/{id}** - детали заказа

## ТЕСТОВЫЕ СЦЕНАРИИ
### Позитивные тесты
- [ ] Валидные данные во всех обязательных полях
- [ ] Граничные значения (минимальное/максимальное количество)
- [ ] Корректные форматы данных (email, phone, dates)

### Негативные тесты
- [ ] Невалидный номер телефона (короткий/длинный/неправильный формат)
- [ ] Несуществующий product_id при добавлении в корзину
- [ ] Пустые обязательные поля
- [ ] Неверные типы данных (string вместо number)

### Проверка ответов
- [ ] HTTP status codes (200, 201, 400, 401, 404, 500)
- [ ] Структура JSON response (соответствие схеме)
- [ ] Сообщения об ошибках на русском языке
- [ ] Время ответа < 2 секунд

## ТЕХНИЧЕСКОЕ ТЕСТИРОВАНИЕ
### Заголовки и кеширование
- [ ] **Content-Type: application/json** в запросах
- [ ] **Authorization: Bearer {token}** в защищенных endpoint'ах
- [ ] Заголовки кеширования для статических данных

### Безопасность
- [ ] Валидация входных данных (SQL injection, XSS)
- [ ] Лимиты запросов (rate limiting)
- [ ] HTTPS обязателен для всех endpoints

---

## ДОПОЛНИТЕЛЬНО
### Мониторинг в DevTools
- [ ] Просмотр сетевых запросов при действиях на сайте
- [ ] Соответствие API calls пользовательским сценариям
- [ ] Отсутствие failed requests в Network tab

### Документация
- [ ] Swagger/OpenAPI документация доступна
- [ ] Описания endpoint'ов, параметров, примеры

---
**Результат:**  
✅ PASS — Все критические endpoints работают корректно  
⚠️ WARN — Есть проблемы с неосновными API  
❌ FAIL — Критические endpoints не работают


**Дата проверки:** 
