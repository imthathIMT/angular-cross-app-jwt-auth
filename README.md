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








🚀 Getting Started
1️⃣ Clone the repo
git clone https://github.com/your-username/angular-cross-app-jwt-auth.git
cd angular-cross-app-jwt-auth
2️⃣ Install dependencies
cd project-1
npm install

cd ../project-2
npm install
3️⃣ Run the apps
Start Project 1 (Login + Dashboard):
cd project-1
ng serve --port 4200
Start Project 2 (Dashboard Only):
cd ../project-2
ng serve --port 4300
🔐 How It Works
🔸 JWT Encoding (in Project 1)
const jwt = await encodeJWT(header, payload, secret);
// Sent via query param: http://localhost:4300?token=...
🔸 Receiving Token (in Project 2)
// Extract token from query param and store in cookie
document.cookie = `token=...; path=/; secure; samesite=strict`;
🔸 AuthGuard & Interceptor (both apps)
AuthGuard checks for token presence (in localStorage or cookies)

Interceptor attaches token to outgoing requests

🔘 Project 2: Buttons
🔙 Return → Removes token cookie, redirects to Project 1 dashboard

🔐 Logout → Clears cookie and sends user to Project 1 login page

