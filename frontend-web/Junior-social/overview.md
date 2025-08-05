
## 🧠 Junior MVP Frontend – Overview

### 📌 Objective:

Create a **multi-role SaaS dashboard** for "Junior" that enables:

* Admins to manage users/roles/settings
* Users to log in and perform role-specific tasks
* Secure internal and external communication between services (REST)

---

## 🗂️ Core Features in MVP

### 1. **Authentication & Authorization**

* ✅ JWT-based auth with login flow
* ✅ Role-based UI rendering (Admin, User, etc.)
* ✅ Frontend reads token from localStorage
* ✅ REST API call to `/api/user/me` to fetch role and details
* 🔒 Protect routes via role-based guards

### 2. **Routing & Layout**

* Uses `react-router-dom` with:

    * `/login` → Login page
    * `/dashboard` → Protected layout
    * Nested routes under `/dashboard/*`
* Global layout with top nav + sidebar (conditionally rendered)

### 3. **User Dashboard**

* 👤 Display user profile info (name, role, etc.)
* 📄 Role-specific dashboard home screen
* ✅ Fetch user data using `restTemplate` call to auth service

### 4. **Admin Panel**

* 🧑‍💼 List users with pagination
* ➕ Add new user (basic form)
* 🛠️ Assign/remove roles
* 🚫 Enable/disable users
* 🔄 Refresh tokens or session control

### 5. **Common Components**

* Toasts for feedback
* Modal for confirmations
* Error boundary / error pages (401, 403, 500)

---

## 🛠️ Tech Stack

| Feature    | Tool                             |
| ---------- | -------------------------------- |
| UI         | React + Vite + SWC               |
| Styling    | TailwindCSS                      |
| Routing    | React Router                     |
| State      | LocalStorage + React Context     |
| Auth       | JWT token stored in localStorage |
| Build Tool | Vite                             |
| Testing    | Vitest (optional)                |
| Linting    | ESLint                           |
| CI/CD      | GitHub Actions (provided above)  |

---

## 🔒 Security MVP (Frontend)

* ✅ Token stored in `localStorage` (consider httpOnly cookie if needed later)
* ✅ Add token to `Authorization: Bearer <token>` header in all API calls
* ✅ Block unauthorized routes if no valid user or token
* 🔁 Token expiration handling (optional refresh logic MVP+)
* ❌ Disable all CORS protection on dev for local REST access

---

## 🔄 Communication with Backend

* Frontend fetches data from:

    * `/api/user/me` (for auth)
    * `/api/users/*` (for admin panel)
* Internally, backend uses `RestTemplate` to communicate between microservices.
* You’ve set allowed origin to `http://localhost:8082` from backend for dev.

---

## 🔄 MVP Flow

1. ✅ **Login page** — Enter credentials → POST `/api/auth/login`
2. ✅ On success, token saved to `localStorage`
3. ✅ Token used to GET `/api/user/me` to retrieve user info and roles
4. ✅ Role-based dashboard UI rendered
5. ✅ Admins can manage users
6. ✅ Users can see their profile / perform role tasks

---

## 🧪 Bonus: Test Plan (Optional for MVP)

| Feature    | Test                                          |
| ---------- | --------------------------------------------- |
| Login      | Valid/Invalid credentials                     |
| Token      | Expired/missing token redirects to `/login`   |
| Routing    | Protected routes only accessible if logged in |
| Roles      | Only admins can access `/dashboard/admin`     |
| API Errors | Show toast + retry option                     |

---

