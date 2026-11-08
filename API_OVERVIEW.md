# 🔌 Технічна документація API (MedReminder Services)

Цей документ містить приклад опису REST API endpoints, які використовуються мобільним застосунком для синхронізації даних з сервером.

Базовий URL: https://api.medreminder.app/v1

---

## 📑 Список Endpoints

### 1. Отримання списку ліків користувача

- HTTP Метод: GET
- URL: /medicines
- Заголовки (Headers): 
  - Authorization: Bearer <your_token>

Приклад успішної відповіді (200 OK):
{
  "status": "success",
  "data": [
    {
      "id": 101,
      "name": "Ібупрофен",
      "dosage": "200 мг",
      "times": ["08:00", "20:00"],
      "pills_left": 24
    },
    {
      "id": 102,
      "name": "Вітамін C",
      "dosage": "500 мг",
      "times": ["12:00"],
      "pills_left": 10
    }
  ]
}

---

### 2. Додавання нового медикаменту

- HTTP Метод: POST
- URL: /medicines
- Заголовки:
  - Content-Type: application/json
  - Authorization: Bearer <your_token>

Приклад тіла запиту (Request Body):
{
  "name": "Омега-3",
  "dosage": "1 капсула",
  "times": ["09:00"],
  "total_pills": 30
}

Приклад успішної відповіді (201 Created):
{
  "status": "created",
  "message": "Препарат успішно додано",
  "medicine_id": 103
}

---

## ⚠️ Коди відповідей та помилок

| Код | Статус | Опис |
|---|---|---|
| 200 | OK | Запит виконано успішно. |
| 201 | Created | Новий ресурс успішно створено. |
| 400 | Bad Request | Некоректні вхідні дані (наприклад, не вказано назву ліку). |
| 401 | Unauthorized | Відсутній або недійсний токен авторизації. |
| 404 | Not Found | Запитуваний ресурс або ліки не знайдені. |
| 500 | Internal Server Error | Помилка на боці сервера. |
