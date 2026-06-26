# Kontrak API (API Contracts)

> **📌 INI ADALAH SUMBER KEBENARAN TUNGGAL.** Tipe frontend dan DTO backend HARUS mencerminkan kontrak ini. Jika ada ketidaksesuaian, kontrak ini yang menang.

## Base URL

```
Development: http://localhost:3001
```

## Format Response Standar

### Sukses — Single Item

```json
{
  "data": {
    "id": "uuid",
    "title": "string",
    "description": "string | null",
    "status": "active | completed",
    "priority": "low | medium | high",
    "createdAt": "ISO 8601",
    "updatedAt": "ISO 8601"
  }
}
```

### Sukses — List (Paginated)

```json
{
  "data": [ /* array of todo objects */ ],
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 42,
    "totalPages": 5
  }
}
```

### Error

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Judul wajib diisi",
    "details": [
      { "field": "title", "message": "title should not be empty" }
    ]
  }
}
```

### Error Codes

| HTTP Status | Code | Keterangan |
|---|---|---|
| 400 | `VALIDATION_ERROR` | Input tidak valid |
| 404 | `NOT_FOUND` | Todo tidak ditemukan |
| 422 | `BUSINESS_RULE_VIOLATION` | Melanggar aturan bisnis (misal: edit todo completed) |
| 429 | `RATE_LIMIT_EXCEEDED` | Terlalu banyak request |
| 500 | `INTERNAL_ERROR` | Error server tidak terduga |

---

## Endpoints

### 1. GET /todos — Daftar Todo

**Query Parameters:**

| Param | Tipe | Default | Keterangan |
|---|---|---|---|
| `page` | number | 1 | Nomor halaman |
| `limit` | number | 10 | Item per halaman (maks 50) |
| `status` | string | — | Filter: `active`, `completed` |
| `priority` | string | — | Filter: `low`, `medium`, `high` |
| `search` | string | — | Cari berdasarkan judul (case-insensitive, partial match) |
| `sort` | string | `createdAt` | Urutkan berdasarkan: `createdAt`, `updatedAt`, `title`, `priority` |
| `order` | string | `DESC` | Arah urutan: `ASC`, `DESC` |

**Response:** `200 OK`

```json
{
  "data": [
    {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "title": "Beli susu",
      "description": "Di supermarket dekat rumah",
      "status": "active",
      "priority": "high",
      "createdAt": "2026-06-26T10:00:00.000Z",
      "updatedAt": "2026-06-26T10:00:00.000Z"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 1,
    "totalPages": 1
  }
}
```

### 2. GET /todos/:id — Detail Todo

**Response:** `200 OK`

```json
{
  "data": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "title": "Beli susu",
    "description": "Di supermarket dekat rumah",
    "status": "active",
    "priority": "high",
    "createdAt": "2026-06-26T10:00:00.000Z",
    "updatedAt": "2026-06-26T10:00:00.000Z"
  }
}
```

**Error:** `404 NOT_FOUND` jika id tidak ada.

### 3. POST /todos — Buat Todo

**Request Body:**

```json
{
  "title": "Beli susu",
  "description": "Di supermarket dekat rumah",
  "priority": "high"
}
```

| Field | Tipe | Wajib | Keterangan |
|---|---|---|---|
| `title` | string | ✅ | 1-200 karakter |
| `description` | string | ❌ | Maks 1000 karakter |
| `priority` | string | ❌ | `low`, `medium`, `high` (default: `medium`) |

**Response:** `201 Created`

```json
{
  "data": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "title": "Beli susu",
    "description": "Di supermarket dekat rumah",
    "status": "active",
    "priority": "high",
    "createdAt": "2026-06-26T10:00:00.000Z",
    "updatedAt": "2026-06-26T10:00:00.000Z"
  }
}
```

**Error:** `400 VALIDATION_ERROR` jika validasi gagal.

### 4. PUT /todos/:id — Ubah Todo

**Request Body:**

```json
{
  "title": "Beli susu dan roti",
  "description": "Di supermarket dekat rumah (update)",
  "status": "active",
  "priority": "medium"
}
```

| Field | Tipe | Wajib | Keterangan |
|---|---|---|---|
| `title` | string | ❌ | 1-200 karakter (jika diisi) |
| `description` | string | ❌ | Maks 1000 karakter |
| `status` | string | ❌ | `active`, `completed` |
| `priority` | string | ❌ | `low`, `medium`, `high` |

**Response:** `200 OK` (sama seperti GET detail)

**Error:**
- `404 NOT_FOUND` jika id tidak ada
- `422 BUSINESS_RULE_VIOLATION` jika todo sudah completed

### 5. DELETE /todos/:id — Hapus Todo (Soft Delete)

**Response:** `200 OK`

```json
{
  "data": {
    "message": "Todo berhasil dihapus"
  }
}
```

**Error:** `404 NOT_FOUND` jika id tidak ada.

---

## Tipe TypeScript (Referensi)

Tipe berikut adalah representasi TypeScript dari kontrak API di atas. Frontend dan backend masing-masing mendefinisikan tipe ini secara independen — tetapi HARUS cocok dengan kontrak ini.

```typescript
// Enums
type TodoStatus = 'active' | 'completed';
type TodoPriority = 'low' | 'medium' | 'high';

// Todo Entity
interface Todo {
  id: string;
  title: string;
  description: string | null;
  status: TodoStatus;
  priority: TodoPriority;
  createdAt: string;  // ISO 8601
  updatedAt: string;  // ISO 8601
}

// DTOs
interface CreateTodoDto {
  title: string;        // required, 1-200 chars
  description?: string;  // optional, max 1000 chars
  priority?: TodoPriority; // optional, default 'medium'
}

interface UpdateTodoDto {
  title?: string;
  description?: string;
  status?: TodoStatus;
  priority?: TodoPriority;
}

// Query
interface TodoQueryParams {
  page?: number;
  limit?: number;
  status?: TodoStatus;
  priority?: TodoPriority;
  search?: string;
  sort?: 'createdAt' | 'updatedAt' | 'title' | 'priority';
  order?: 'ASC' | 'DESC';
}

// Response wrappers
interface ApiResponse<T> {
  data: T;
}

interface PaginatedResponse<T> {
  data: T[];
  meta: {
    page: number;
    limit: number;
    total: number;
    totalPages: number;
  };
}

interface ApiError {
  error: {
    code: string;
    message: string;
    details?: Array<{ field: string; message: string }>;
  };
}
```
