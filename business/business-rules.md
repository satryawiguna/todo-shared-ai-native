# Business Rules

## Ownership
- BR-01: User hanya dapat melihat, mengedit, dan menghapus task miliknya sendiri
- BR-02: Tidak ada shared task antar user pada v1

## Task Status
- BR-10: Status task: `todo` → `in_progress` → `done`
- BR-11: Task yang sudah `done` masih dapat di-edit atau dihapus
- BR-12: Due date boleh kosong (optional)

## Validasi
- BR-20: Title task wajib diisi, maksimal 255 karakter
- BR-21: Priority task: `low`, `medium`, `high` (default: `medium`)
- BR-22: Password minimal 8 karakter, harus mengandung huruf dan angka
- BR-23: Email harus unik per user

## Data Retention
- BR-30: Soft delete untuk task (field `deleted_at`)
- BR-31: Hard delete tidak diekspos ke API publik
