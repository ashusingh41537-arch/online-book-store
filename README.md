# 📚 Digital Library System
### Full Stack Project: React JS + Spring Boot + MySQL

> A **soft copy reading platform** — users can browse and read books online for free. No selling, no payments.

---

## 🏗️ Project Structure

```
digital-library-system/
├── 📁 digital-library-backend/     ← Spring Boot REST API
├── 📁 digital-library-frontend/    ← React JS Web App
└── 📁 database/
    └── schema.sql                  ← MySQL setup script
```

---

## ⚙️ Prerequisites

Make sure you have these installed before starting:

| Tool | Version | Download |
|------|---------|----------|
| ☕ Java JDK | 17+ | https://adoptium.net |
| 🔧 Maven | 3.8+ | https://maven.apache.org |
| 🐬 MySQL | 8.0+ | https://dev.mysql.com |
| 🟢 Node.js | 18+ | https://nodejs.org |
| 💻 VS Code | Latest | https://code.visualstudio.com |

---

## 🚀 Step-by-Step Setup Guide

### 📌 STEP 1 — Setup MySQL Database

1. Open **MySQL Workbench** or your MySQL client
2. Run the SQL file:
   ```sql
   -- In MySQL Workbench or CLI:
   source /path/to/digital-library-system/database/schema.sql
   ```
   OR copy-paste contents of `database/schema.sql` and execute.

3. This creates:
   - `digital_library_db` database
   - `users`, `books`, `book_access` tables
   - Sample books + Admin user

---

### 📌 STEP 2 — Configure Database Credentials

Open this file in VS Code:
```
digital-library-backend/src/main/resources/application.properties
```

Update your MySQL username/password:
```properties
spring.datasource.username=root       ← Change this
spring.datasource.password=root       ← Change this
```

---

### 📌 STEP 3 — Run the Backend (Spring Boot)

**Option A: Using VS Code Terminal**
```bash
# Open terminal in VS Code (Ctrl + `)
# Navigate to backend folder
cd digital-library-backend

# Build and run
mvn spring-boot:run
```

**Option B: Using Maven wrapper**
```bash
cd digital-library-backend
./mvnw spring-boot:run      # Mac/Linux
mvnw.cmd spring-boot:run    # Windows
```

✅ Backend starts at: **http://localhost:8080**

You'll see: `✅ Digital Library Backend is running on http://localhost:8080`

---

### 📌 STEP 4 — Run the Frontend (React)

Open a **new terminal** in VS Code:
```bash
# Navigate to frontend folder
cd digital-library-frontend

# Install dependencies (first time only)
npm install

# Start the development server
npm start
```

✅ Frontend opens at: **http://localhost:3000**

---

## 🔐 Default Login Credentials

| Role | Email | Password |
|------|-------|----------|
| 👑 Admin | admin@library.com | admin123 |
| 👤 User | Register new account | (your choice) |

---

## 🌐 API Endpoints Reference

### 🔵 Auth
| Method | URL | Description |
|--------|-----|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login & get JWT token |

### 🔵 Books (Public)
| Method | URL | Description |
|--------|-----|-------------|
| GET | `/api/books` | Get all books |
| GET | `/api/books/{id}` | Get book by ID |
| GET | `/api/books/search?keyword=X` | Search books |
| GET | `/api/books/category/{cat}` | Filter by category |

### 🔵 Access (Auth Required)
| Method | URL | Description |
|--------|-----|-------------|
| POST | `/api/access/record` | Record book reading |
| GET | `/api/access/history/{userId}` | Get reading history |
| PUT | `/api/access/page` | Update last page |

### 🔵 Admin (ADMIN Role Only)
| Method | URL | Description |
|--------|-----|-------------|
| GET | `/api/admin/dashboard` | Dashboard stats |
| POST | `/api/admin/books` | Add new book |
| PUT | `/api/admin/books/{id}` | Update book |
| DELETE | `/api/admin/books/{id}` | Delete book |
| GET | `/api/admin/users` | List all users |
| DELETE | `/api/admin/users/{id}` | Delete user |

---

## 📦 Tech Stack Summary

```
Frontend                    Backend                   Database
─────────                   ───────                   ────────
React JS 18                 Spring Boot 3.2           MySQL 8.0
React Router v6             Spring Security           JPA / Hibernate
Axios                       JWT Authentication
React Toastify              BCrypt Encryption
CSS3 (Custom)               Maven
```

---

## 🗂️ Key Feature Pages

| Page | URL | Access |
|------|-----|--------|
| 🏠 Home | / | Public |
| 📚 Browse Books | /books | Public |
| 📖 Book Details | /books/:id | Public |
| 📄 Read Book | /books/:id/read | Login Required |
| ⚙️ Admin Dashboard | /admin | Admin Only |
| 📤 Upload Book | /admin/books/upload | Admin Only |
| 📋 Manage Books | /admin/books | Admin Only |
| 👥 Manage Users | /admin/users | Admin Only |

---

## ❗ Troubleshooting

### Backend won't start?
- ✅ Check MySQL is running
- ✅ Check credentials in `application.properties`
- ✅ Make sure port 8080 is free: `netstat -ano | findstr :8080`

### Frontend won't connect to backend?
- ✅ Make sure backend is running first
- ✅ Check CORS: backend allows `http://localhost:3000`
- ✅ Check `axiosConfig.js` baseURL is `http://localhost:8080`

### "Access Denied" errors?
- ✅ Login first to get JWT token
- ✅ Admin routes require ADMIN role
- ✅ Token stored in localStorage — check Browser DevTools > Application

### npm install fails?
```bash
npm install --legacy-peer-deps
```

---

## 🎯 VS Code Recommended Extensions

Install these for better development experience:
- **Spring Boot Extension Pack** — Spring Boot support
- **Java Extension Pack** — Java language support  
- **ES7+ React/Redux Snippets** — React shortcuts
- **Prettier** — Code formatting
- **Thunder Client** — API testing inside VS Code

---

## 📝 Notes

- PDFs are served via URL — upload your PDFs to any hosting (Google Drive, Dropbox, etc.) and paste the direct link
- The system uses **JWT tokens** (24-hour expiry by default)
- Books marked as "Free" — no payment system included by design
- Admin can add books with cover images via image URL

---

*Happy Reading! *
