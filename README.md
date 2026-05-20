# TaskFlow — Team Task Manager

A full-stack team task management web application with role-based access control (Admin / Member).

---

## Description

TaskFlow is a collaborative task management platform built for teams. It supports project creation, task assignment, progress tracking, activity logging, and team management secured with JWT authentication and role-based permissions.

---

## Tech Stack

| Technology | Stack |
|---|---|
| Frontend | React 18 + Vite + CSS-in-JS |
| Backend | Node.js + Express.js |
| Authentication | JWT (JSON Web Tokens) |
| Database | SQLite |
| Deployment | Railway |

---

## Features

- **Authentication** — Signup, Login, Logout, Reset Password
- **Role-Based Access** — Admin vs Member permissions
- **Project Management** — Create, edit, delete, assign members
- **Task Management** — Create, assign, track status, add comments
- **Dashboard** — Stats, progress indicators, overdue alerts
- **Team Management** — View progress, change roles, remove members
- **Reports & Activity Logs** — Full audit trail of all actions

---

## Authentication & Role-Based Access

| Role | Permissions |
|---|---|
| Admin | Full access — manage projects, tasks, users, roles |
| Member | View assigned tasks, update task status, add comments |

---

## REST API Endpoints

### Auth — `/api/auth`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| POST | `/signup` | Public | Register a new user |
| POST | `/login` | Public | Login and receive JWT |
| GET | `/me` | Auth | Get current logged-in user |
| PUT | `/profile` | Auth | Update name, email, bio |
| PUT | `/password` | Auth | Change password |

---

### Projects — `/api/projects`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/` | Auth | Get all projects |
| POST | `/` | Admin | Create a new project |
| PUT | `/:id` | Admin | Update project details |
| DELETE | `/:id` | Admin | Delete a project |

---

### Tasks — `/api/tasks`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/` | Auth | Get all tasks |
| POST | `/` | Admin | Create a new task |
| PUT | `/:id` | Auth | Update task |
| DELETE | `/:id` | Admin | Delete task |
| POST | `/:id/comments` | Auth | Add task comment |
| GET | `/logs` | Auth | Fetch activity logs |

---

### Users — `/api/users`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/` | Admin | List all team members |
| PUT | `/:id/role` | Admin | Change user role |
| DELETE | `/:id` | Admin | Remove a member |

---

## Team Accounts

| Name | Email | Password | Role |
|---|---|---|---|
| Arjun Sharma | arjun@taskflow.com | arjun@123 | Admin |
| Tejaswee Thorat | tejaswee@taskflow.com | tejas@123 | Member |
| Rohan Kulkarni | rohan@taskflow.com | rohan@123 | Member |
| Priya Desai | priya@taskflow.com | priya@123 | Member |

---

## Local Setup Instructions

### Prerequisites

- Node.js v18+
- npm v9+
- Git

---

### 1. Clone Repository

```bash
git clone https://github.com/tejasweethorat-git/taskmanager.git
cd taskmanager
```

---

### 2. Setup Backend

```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

Backend runs on: `http://localhost:5000`

---

### 3. Setup Frontend

Open a new terminal:

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on: `http://localhost:5173`

---

> The database file (`taskflow.db`) is automatically created on first run and loaded with seed data.

---

## Project Structure

```
taskflow/
├── frontend/
│   ├── src/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   └── package.json
│
├── backend/
│   ├── src/
│   │   ├── index.js
│   │   ├── db/
│   │   │   ├── init.js
│   │   │   └── seed.js
│   │   ├── middleware/
│   │   │   └── auth.js
│   │   └── routes/
│   │       ├── auth.js
│   │       ├── users.js
│   │       ├── projects.js
│   │       └── tasks.js
│   ├── .env.example
│   └── package.json
│
└── README.md
```

---

## Railway Deployment

1. Push repository to GitHub
2. Go to Railway → New Project → Deploy from GitHub
3. Add frontend and backend services
4. Configure environment variables from `.env.example`
5. Railway auto-detects Node.js and deploys automatically

---

## Validation Implemented

- Required fields validation
- Email uniqueness validation
- Password minimum length validation
- Restricted task status updates for Members
- Role validation (Admin / Member only)
- Admin self-delete protection
- JWT token verification on protected routes

---

## Author

| | |
|---|---|
| **Name** | Tejaswee Thorat |
| **Email** | tejasweethorat76@gmail.com |
| **Project** | Team Task Manager |
