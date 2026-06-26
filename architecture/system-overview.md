# System Overview

## Architecture Style
REST API + SPA (Single Page Application)

## Components

```
[Browser]
    ↓ HTTPS
[Next.js Frontend — todo-frontend]
    ↓ REST API (JSON)
[Node.js API — todo-api]
    ↓ SQL
[MySQL Database]
```

## Deployment Target (v1)
- Frontend: Vercel
- Backend: Railway / Render
- Database: PlanetScale / Railway MySQL

## Communication
- Frontend → Backend: REST API dengan JWT ******
- Semua response menggunakan format JSON standar (lihat api-contracts.md)
- Error menggunakan format RFC 7807 (Problem Details)
