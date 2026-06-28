# Gambaran Sistem (System Overview)

## Stack Teknologi

```
┌──────────────────────────────────────────────────────────────────┐
│                         Pengguna                                 │
│                   (Browser / Laptop)                             │
└────────┬──────────────────────────────┬──────────────────────────┘
         │                              │
         ▼                              ▼
┌────────────────────────┐   ┌────────────────────────┐
│   Landing Page         │   │   Dashboard            │
│   (Website Marketing)  │   │   (Aplikasi Utama)     │
│   Next.js 15           │   │   Next.js 15           │
│                        │   │                        │
│   local     :3000      │   │   local     :3001      │
│   dev       :3002      │   │   dev       :3003      │
│   prod      :3004      │   │   prod      :3005      │
└────────┬───────────────┘   └─────────┬──────────────┘
         │                             │
         │        HTTP / JSON          │
         └──────────┬──────────────────┘
                    ▼
┌──────────────────────────────────────────────────────────────────┐
│                Nest.js (Backend API)                             │
│  • REST API  • TypeORM + MySQL  • class-validator                │
│  • Swagger/OpenAPI  • Helmet, CORS, Rate Limiting                │
│                                                                  │
│  local :5000  │  dev :5001  │  prod :5002                        │
└───────────────────────┬──────────────────────────────────────────┘
                        │ TCP :3306 — local MySQL | AWS RDS :3306 (todo_dev / todo_prod)
                        ▼
┌──────────────────────────────────────────────────────────────────┐
│                   MySQL 8 (Database)                             │
│  • Tabel: todos  • Soft delete support                           │
│  • local: MySQL lokal  • dev/prod: AWS RDS (1 instance)          │
└──────────────────────────────────────────────────────────────────┘
```

## Environment Matrix

| Environment | Landing Page | Dashboard | Backend API | Database | Docker |
|---|---|---|---|---|---|
| **local** | `:3000` | `:3001` | `:5000` | `:3306` — `todo_db` (MySQL lokal) | ❌ Manual (`pnpm dev`) |
| **development** | `:3002` | `:3003` | `:5001` | `:3306` — `todo_dev` (AWS RDS, user: `root_dev`) | ✅ `docker compose up` |
| **production** | `:3004` | `:3005` | `:5002` | `:3306` — `todo_prod` (AWS RDS, user: `root`) | ✅ `docker compose -f compose.prod.yml up` |

> Port antar environment berbeda agar local (manual) dan development (Docker) dapat berjalan bersamaan tanpa konflik. Database dev dan prod menggunakan 1 AWS RDS instance dengan database berbeda.

## Frontend Monorepo Structure

Frontend dibangun dengan **clean directory architecture** dan **monorepo** (Turborepo/Nx):

```
todo-app-ai-native-orchestration/
├── apps/
│   ├── dashboard/          # Next.js 15 — Aplikasi utama Todo
│   │   ├── src/
│   │   │   ├── app/        # App Router (Server Components)
│   │   │   ├── components/ # UI components
│   │   │   ├── hooks/      # Custom hooks (React Query, Zustand)
│   │   │   ├── services/   # API client (Axios)
│   │   │   └── types/      # TypeScript types (dari api-contracts.md)
│   │   └── package.json
│   └── landing-page/       # Next.js 15 — Website marketing
│       ├── src/
│       │   └── app/        # Static pages + SEO
│       └── package.json
└── packages/
    └── shared/             # Shared types, utils, constants
        └── src/
            └── types/      # Todo types shared across apps
```

## Model Deployment

### Local (Manual — tanpa Docker)

```bash
# Terminal 1: Backend API
cd todo-api-ai-native-orchestration
pnpm start:dev          # → http://localhost:5000

# Terminal 2: Dashboard
cd todo-app-ai-native-orchestration/apps/dashboard
pnpm dev                # → http://localhost:3001

# Terminal 3: Landing Page
cd todo-app-ai-native-orchestration/apps/landing-page
pnpm dev                # → http://localhost:3000
```

### Development & Production (Docker)

```yaml
# compose.yml (development)
services:
  landing-page:   # Next.js — port 3002
  dashboard:      # Next.js — port 3003
  backend:        # Nest.js — port 5001
  # Database tidak di-Docker — pakai AWS RDS (db: todo_dev, user: root_dev, port: 3306)
```

```yaml
# compose.prod.yml (production)
services:
  landing-page:   # Next.js — port 3004
  dashboard:      # Next.js — port 3005
  backend:        # Nest.js — port 5002
  # Database tidak di-Docker — pakai AWS RDS (db: todo_prod, user: root, port: 3306)
```

Setiap service memiliki `Dockerfile` multi-stage sendiri untuk build yang optimal.

## Aliran Data

```
[Browser] ──GET /todos──▶ [Next.js Server] ──GET /todos──▶ [Nest.js API] ──SELECT──▶ [MySQL]
                                                                                      │
[Browser] ◀──JSON────── [Next.js Server] ◀──JSON─────── [Nest.js API] ◀────rows─────┘
```

- **Read path:** Browser → Next.js (Server Component fetch) → Nest.js → MySQL → response
- **Write path:** Browser → Next.js (Client Component mutation) → Axios → Nest.js → TypeORM → MySQL → response → React Query cache invalidation → UI update
