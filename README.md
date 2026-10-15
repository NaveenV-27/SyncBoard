# SyncBoard

**GitHub:** https://github.com/NaveenV-27/SyncBoard.git  
**Author:** Naveen

## Overview
SyncBoard is a real‑time task‑management platform that lets teams collaborate on Kanban boards with instant updates. Users can create teams, assign tasks, move columns via drag‑and‑drop, and receive live notifications—all without manual page refreshes.

## Tech Stack
- **Frontend:** React 19, Vite, Tailwind CSS, Framer Motion, @dnd‑kit (drag‑and‑drop), Pusher‑JS, React Router 7
- **Backend:** Node.js 18+, Express 5, Prisma ORM with PostgreSQL, Pusher (server), JWT + bcryptjs for auth
- **Database:** PostgreSQL
- **Real‑time:** Pusher (managed WebSockets) for optimistic UI updates and broadcasting

## Key Features
- ⚡ Real‑time synchronization via Pusher (task updates, drag‑and‑drop, notifications)
- 🛡️ Role‑based access control (Admin, Member, Viewer)
- 🚀 Zero‑signup “recruiter test drive” demo mode
- 📊 Switch between Kanban board and calendar views
- 🔔 Live in‑app notification panel
- 🎨 Glassmorphic UI with micro‑animations
- 🖱️ Intuitive task cards with priority, due dates, assignees

## Getting Started
### Prerequisites
- Node.js ≥ 18
- PostgreSQL (local or remote URI)
- Pusher account (for app ID, key, secret, cluster)

### 1. Clone the repo
```bash
git clone https://github.com/NaveenV-27/SyncBoard.git
cd SyncBoard
```

### 2. Backend setup
```bash
cd backend
npm install
# Create backend/.env with:
# PORT=8000
# DATABASE_URL="postgresql://user:password@localhost:5432/syncboard?schema=public"
# JWT_SECRET="your_super_secret_key"
# PUSHER_APP_ID="your_app_id"
# PUSHER_KEY="your_key"
# PUSHER_SECRET="your_secret"
# PUSHER_CLUSTER="mt1"
npx prisma db push
npx prisma generate
npm start   # runs on http://localhost:8000
```

### 3. Frontend setup (new terminal)
```bash
cd ../frontend
npm install
# Create frontend/.env (optional) with:
# VITE_API_URL=http://localhost:8000
# VITE_PUSHER_KEY=your_pusher_key
# VITE_PUSHER_CLUSTER=mt1
npm run dev   # runs on http://localhost:5173
```

## API Overview (base URL `http://localhost:8000`)
- **Auth:** `POST /api/signup`, `POST /api/login`, `POST /api/test-login` (demo), `GET /api/me`, `PUT /api/me`
- **Teams:** `GET /api/teams`, `POST /api/teams`, `POST /api/teams/join`, `POST /api/teams/approve`, `POST /api/teams/reject`, `PUT /api/teams/role`, `GET /api/teams/:teamId`
- **Tasks:** `POST /api/tasks`, `GET /api/tasks/team/:teamId`, `PUT /api/tasks/:taskId`, `DELETE /api/tasks/:taskId`
- **Notifications:** `GET /api/notifications`, `PUT /api/notifications/:id/read`, `PUT /api/notifications/read-all`, `DELETE /api/notifications/:id`

## License
MIT License – see `LICENSE` file.

---
*If you have questions or want to contribute, open an issue or pull request on the GitHub repository above.*