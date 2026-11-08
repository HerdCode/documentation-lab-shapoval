# 🔌 Технічна документація API (MedReminder Services)

Цей документ містить приклад опису REST API endpoints, які використовуються мобільним застосунком для синхронізації даних з сервером.

Базовий URL: `https://api.medreminder.app/v1`

---

## 📑 Список Endpoints

### 1. Отримання списку ліків користувача

- **HTTP Метод:** `GET`
- **URL:** `/medicines`
- **Заголовки (Headers):** 
  - `Authorization: Bearer <your_token>`

#### Приклад успішної відповіді (`200 OK`):
```json
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

- **HTTP Метод:** `POST`
- **URL:** `/medicines`
- **Заголовки:**
  - `Content-Type: application/json`
  - `Authorization: Bearer <your_token>`

#### Приклад тіла запиту (Request Body):
```json
{
  "name": "Омега-3",
  "dosage": "1 капсула",
  "times": ["09:00"],
  "total_pills": 30
}
