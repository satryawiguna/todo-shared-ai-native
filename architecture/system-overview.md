# Gambaran Sistem (System Overview)

## Stack Teknologi

```
┌─────────────────────────────────────────────────┐
│                   Pengguna                       │
│              (Browser / Laptop)                   │
└─────────────────┬───────────────────────────────┘
                  │ HTTPS
                  ▼
┌─────────────────────────────────────────────────┐
│           Next.js 15 (Frontend)                  │
│  • App Router + Server Components                │
│  • TanStack React Query (server state)           │
│  • Zustand (client state)                        │
│  • Axios (HTTP client)                           │
│  • Tailwind CSS (styling)                        │
│  • Port: 3000                                    │
└─────────────────┬───────────────────────────────┘
                  │ HTTP / JSON
                  ▼
┌─────────────────────────────────────────────────┐
│           Nest.js (Backend API)                  │
│  • REST API                                      │
│  • TypeORM + MySQL                               │
│  • class-validator (DTO validation)              │
│  • Swagger/OpenAPI docs                          │
│  • Helmet, CORS, Rate Limiting                   │
│  • Port: 3001                                    │
└─────────────────┬───────────────────────────────┘
                  │ TCP 3306
                  ▼
┌─────────────────────────────────────────────────┐
│              MySQL 8 (Database)                   │
│  • Tabel: todos                                  │
│  • Soft delete support                           │
│  • Port: 3306                                    │
└─────────────────────────────────────────────────┘
```

## Model Deployment

Setiap komponen dijalankan via **Docker**:

```yaml
# docker-compose (development)
services:
  frontend:    # Next.js 15 — port 3000
  backend:     # Nest.js — port 3001
  database:    # MySQL 8 — port 3306
```

Untuk production, frontend dan backend masing-masing memiliki `Dockerfile` multi-stage sendiri.

## Aliran Data

```
[Browser] ──GET /todos──▶ [Next.js Server] ──GET /todos──▶ [Nest.js API] ──SELECT──▶ [MySQL]
                                                                                      │
[Browser] ◀──JSON────── [Next.js Server] ◀──JSON─────── [Nest.js API] ◀────rows─────┘
```

- **Read path:** Browser → Next.js (Server Component fetch) → Nest.js → MySQL → response
- **Write path:** Browser → Next.js (Client Component mutation) → Axios → Nest.js → TypeORM → MySQL → response → React Query cache invalidation → UI update
