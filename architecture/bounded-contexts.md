# Bounded Contexts (DDD)

## Konteks Utama

```
┌──────────────────────┐    ┌──────────────────────┐
│    Todo Context       │    │    User Context       │
│  (MVP — diimplementasikan)│    │  (v1 — mendatang)      │
│                      │    │                      │
│  • Todo Entity       │    │  • User Entity       │
│  • TodoService       │    │  • AuthService       │
│  • TodoController    │    │  • AuthController    │
│  • CRUD + Filter     │    │  • Register/Login    │
│                      │    │  • JWT Guard         │
└──────────┬───────────┘    └──────────┬───────────┘
           │                           │
           │      ┌────────────────────┘
           │      │ (v1: Todo belongs to User)
           ▼      ▼
┌─────────────────────────────────────────────────┐
│            Shared Kernel                         │
│  • DTO conventions                              │
│  • Validation patterns                          │
│  • Error response format                        │
│  • Pagination standard                          │
└─────────────────────────────────────────────────┘
```

## Todo Context (MVP)

**Tanggung jawab:** Mengelola siklus hidup Todo — buat, baca, ubah, hapus, filter, cari.

**Agregat root:** `Todo`

**Entitas:**
- `Todo` — id, title, description, status, priority, createdAt, updatedAt, deletedAt

**Value objects:**
- `TodoStatus` — enum: active, completed
- `TodoPriority` — enum: low, medium, high

**Aturan bisnis:** Lihat `business/business-rules.md`

## User Context (v1)

**Tanggung jawab:** Autentikasi, otorisasi, manajemen profil.

**Agregat root:** `User`

**Hubungan dengan Todo Context:** Satu User memiliki banyak Todo (one-to-many). User context adalah upstream — Todo context downstream.

## Notification Context (v2)

**Tanggung jawab:** Mengirim notifikasi (email, in-app) berdasarkan event Todo.

**Event yang didengarkan:** `TodoCreated`, `TodoDueSoon`, `TodoCompleted`
