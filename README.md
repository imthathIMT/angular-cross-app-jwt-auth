# Angular Cross-App JWT Auth

This repository contains **two Angular 19 projects** that demonstrate **secure JWT-based navigation between apps** using **query parameters**, **cookies**, **Auth Guards**, and **Interceptors**.

## 🔗 Projects Overview

| Project Name | Description |
|--------------|-------------|
| `project-1`  | Login + Dashboard + Navigates to Project 2 with a secure JWT token in query params |
| `project-2`  | Dashboard-only app that receives and decodes the JWT token, stores it in cookies, and secures routes using AuthGuard & Interceptor |

---

## 🧠 Features

✅ JWT creation with HMAC-SHA256  
✅ Base64URL encoding & decoding (secure transfer)  
✅ Navigation with JWT via query params  
✅ Cookie storage for tokens (Project 2)  
✅ AuthGuard + Interceptor in both apps  
✅ "Return" and "Logout" buttons in Project 2  
✅ Logout clears both cookie and localStorage  
✅ Route protection across apps  

---

## 🏗 Folder Structure

```bash
angular-cross-app-jwt-auth/
├── project-1/          # Login + Dashboard
│   └── src/app/
│       ├── login/
│       ├── dashboard/
│       ├── jwt-utils.service.ts
│       └── logout.component.ts
├── project-2/          # Dashboard + Cookie Auth
│   └── src/app/
│       ├── app.component.ts
│       ├── auth.guard.ts
│       ├── auth.interceptor.ts
│       ├── jwt-utils.service.ts
├── README.md



```markdown
# 🚀 Angular Cross-App JWT Authentication

This project demonstrates cross-application authentication using JWTs in Angular. It features two separate apps:

- **Project 1**: Login + Dashboard  
- **Project 2**: Dashboard Only (accessed with a JWT token)

---

## 🛠️ Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/angular-cross-app-jwt-auth.git
cd angular-cross-app-jwt-auth
```

### 2️⃣ Install Dependencies

```bash
cd project-1
npm install

cd ../project-2
npm install
```

### 3️⃣ Run the Applications

**Start Project 1 (Login + Dashboard):**

```bash
cd project-1
ng serve --port 4200
```

**Start Project 2 (Dashboard Only):**

```bash
cd ../project-2
ng serve --port 4300
```

---

## 🔐 How It Works

### 🔸 JWT Encoding (in Project 1)

```ts
const jwt = await encodeJWT(header, payload, secret);
```

- The token is sent via a query parameter:
  ```
  http://localhost:4300?token=...
  ```

### 🔸 Receiving Token (in Project 2)

- Extract token from query param and store in cookie:

```js
document.cookie = `token=...; path=/; secure; samesite=strict`;
```

### 🔸 AuthGuard & Interceptor (Both Projects)

- **AuthGuard**: Checks for token presence (in `localStorage` or cookies)
- **Interceptor**: Attaches token to outgoing HTTP requests

---

## 🔘 Project 2: Buttons

- **🔙 Return** → Removes token cookie, redirects to Project 1 dashboard  
- **🔐 Logout** → Clears cookie and sends user to Project 1 login page

---

## 📂 Folder Structure

```
angular-cross-app-jwt-auth/
├── project-1/     # Login + Dashboard
└── project-2/     # Token-based Dashboard
```

---

## 📌 Notes

- Ensure both apps run on different ports (4200 and 4300)
- Cookies are stored with `secure` and `samesite=strict` flags for enhanced security
- Useful for micro-frontend or multi-portal architecture with centralized authentication


---

Let me know if you want to update the GitHub URL, customize styling, or add images/screenshots!
