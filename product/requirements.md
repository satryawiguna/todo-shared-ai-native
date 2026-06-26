# Functional Requirements

## Authentication
- FR-01: User dapat registrasi dengan email + password
- FR-02: User dapat login dan mendapatkan JWT token
- FR-03: User dapat logout dan token di-invalidate
- FR-04: Token refresh otomatis sebelum expired

## Task Management
- FR-10: User dapat membuat task dengan title, description, due date, priority
- FR-11: User dapat mengedit task miliknya
- FR-12: User dapat menghapus task miliknya
- FR-13: User dapat mengubah status task (todo, in_progress, done)
- FR-14: User dapat memfilter task berdasarkan status dan priority
- FR-15: User dapat mencari task berdasarkan keyword

## Non-Functional Requirements
- NFR-01: API response time < 200ms untuk operasi CRUD standar
- NFR-02: Password di-hash menggunakan bcrypt (cost factor >= 12)
- NFR-03: Semua endpoint (kecuali auth) memerlukan valid JWT
- NFR-04: Input validation di frontend dan backend
