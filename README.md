# Інтеграція клієнтської частини з RESTful API
# Мета
# Підключити користувацький інтерфейс до реального серверного API. Ознайомитися з підходами до організації HTTP-запитів через Axios, зберігання токенів доступу, обробки помилок, роботи з .env-змінними. Забезпечити повноцінну взаємодію клієнтської частини з бекендом.
# Завдання
# Використовуючи реалізовану у попередньому завданні клієнтську частину (інтерфейс для роботи з сутністю Post), внести такі зміни:
## 1. Налаштування змінних оточення:
- У корені проєкту створити файл .env
- Додати до нього такі змінні:
VITE_API_BASE_URL=http://localhost:4000/v1
VITE_API_AUTH_TOKEN=your_jwt_token_here
# Реалізувати використання цих змінних у конфігурації Axios
## 2. Створити конфігурацію Axios:
- Створити окремий файл (наприклад, src/api/axios.ts)
- Налаштувати базовий baseURL, заголовок Content-Type, токен авторизації:
- Реалізувати обробку помилок через інтерцептор (наприклад, логування у консоль або показ повідомлення)
# 3. Замінити мок-функції на реальні HTTP-запити:
- У файлі з API-функціями (src/api/posts.ts або аналогічному) замінити реалізацію:  
getAllEntities() → GET /posts  
getEntityById(id) → GET /posts/:id  
createEntity(data) → POST /posts  
updateEntity(id, data) → PUT /posts/:id  
deleteEntity(id) → DELETE /posts/:id
# Реалізація
- Створено файл .env та додано змінні:  
![image](https://github.com/user-attachments/assets/d2b7ad63-b5df-4b25-97e0-fcf51c481942)  
- Створено axio.ts та в ньому налаштован baseUrl, імпортованні змінні з .env, та реалізована обробка помилок  
![image](https://github.com/user-attachments/assets/4577bc57-d0b8-47ad-bbd4-fbd216038998)  
- Замінив назву mockFunctions на posts.ts, та перероблено реалізацію на використання api створеного в 5 роботі.  
![image](https://github.com/user-attachments/assets/b68fa750-f09a-4ce7-a20a-c9b0086db417)
# Демонстрація результату:
- При створенні post:
![image](https://github.com/user-attachments/assets/586c0c3e-9b18-4c48-8d08-cd7f27e762eb)  
![image](https://github.com/user-attachments/assets/f9f817c6-ff53-458b-ad4d-352b86f8b32a)  
Надсилається POST запит, Post створюється, та повертає на колецію Posts
- При перегляду усієї колекції:  
![image](https://github.com/user-attachments/assets/9e606670-5767-48df-8eb1-525d02a1b94b)  
![image](https://github.com/user-attachments/assets/cb7bb626-15b2-459b-b1e4-4296045cdb66)  
Надсилається GET запит та повертається список posts
- При перегляду одного Post:
![image](https://github.com/user-attachments/assets/27f966ff-9147-4db4-8861-2a37591961b4)
![image](https://github.com/user-attachments/assets/d0fc297e-a636-4c67-885c-99626a074ecf)
Надсилається GET запит (by id) та повертається post
- При зміні Post:
![image](https://github.com/user-attachments/assets/a901db72-00da-4bde-8894-88d0c5ce7ab2)  
![image](https://github.com/user-attachments/assets/01990308-bb7c-4fdd-b0a3-b4232a72dbf9)  
Надсилається PATCH запит, дані успішно оновлені та юзера перенаправляє на сторінку Post з оновленими даними
- При видалені Post:  
![image](https://github.com/user-attachments/assets/90818989-774a-4843-8a3c-9eeb3bea7a7c)
![image](https://github.com/user-attachments/assets/146be398-2fff-491d-ab82-4177c3bbda31)
Надсилається DELETE запит, зі сторінки пропадає Post
# Коментар
В третьому завданні, я би додав пункт на створення конфігураційного файлу, який дозволяє перемикатися між mock-функціями та реальними API-запитами, для того щоб було легше тестувати, без підключення до бекенда.
# Висновок
Під час виконання цієї роботи я інтегрував клієнтську частину з реальним RESTful API, замінивши мок-функції на HTTP-запити з використанням Axios. Налаштував змінні оточення через .env для зберігання базового URL та токена авторизації. Реалізував конфігурацію Axios з обробкою помилок за допомогою інтерцепторів. Також забезпечив повноцінну взаємодію клієнта з бекендом для всіх CRUD-операцій. Робота дозволила краще зрозуміти, як організовувати структуру API-запитів та керувати токенами доступу.








