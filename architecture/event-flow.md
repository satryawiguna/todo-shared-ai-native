# Alur Event (Event Flow)

*Untuk MVP, event bersifat sederhana. Alur async event akan diimplementasikan di v1/v2.*

## Event MVP (Synchronous)

Semua operasi saat ini bersifat **synchronous** — request langsung diproses dan response dikembalikan:

```
POST /todos → validasi → simpan DB → response 201
PUT /todos/:id → validasi → update DB → response 200
DELETE /todos/:id → set deletedAt → response 200
```

## Event v1 (Async)

Ketika autentikasi ditambahkan:

```
UserRegistered
  → payload: { userId, email, timestamp }
  → handler: kirim email verifikasi

TodoCreated
  → payload: { todoId, userId, title, timestamp }
  → handler: update user analytics counter

TodoCompleted
  → payload: { todoId, userId, completedAt }
  → handler: update user statistics
```

## Event v2 (Async)

Ketika notifikasi ditambahkan:

```
TodoDueSoon
  → payload: { todoId, userId, title, dueDate }
  → handler: kirim email pengingat

TodoCompleted
  → payload: { todoId, userId, title, completedAt }
  → handler: kirim notifikasi ke anggota tim (jika ada kolaborasi)
```

## Jaminan Event (untuk v1+)

- **At-least-once delivery** — setiap event dijamin terkirim minimal sekali
- **Idempotency** — handler harus idempotent (event key: `todoId + eventType`)
- **Ordering** — event per todo dijamin terurut berdasarkan timestamp
