# Glosarium (Glossary)

Bahasa di mana-mana (ubiquitous language) yang digunakan di seluruh proyek.

## Entitas Utama

| Istilah | Definisi | Catatan |
|---|---|---|
| **Todo** | Item tugas yang perlu dilakukan pengguna | Entitas utama dalam aplikasi |
| **Judul (Title)** | Nama singkat todo | Wajib, 1-200 karakter |
| **Deskripsi (Description)** | Penjelasan detail todo | Opsional, maks 1000 karakter |

## Status

| Istilah | Definisi |
|---|---|
| **Active** | Todo sedang aktif dan dapat dikerjakan |
| **Completed** | Todo sudah selesai — tidak dapat diedit (immutable) |
| **Archived** | Todo diarsipkan — tidak muncul di daftar default (fitur v1) |

## Prioritas

| Istilah | Definisi |
|---|---|
| **Low** | Prioritas rendah |
| **Medium** | Prioritas sedang — default |
| **High** | Prioritas tinggi |

## Operasi

| Istilah | Definisi |
|---|---|
| **Soft Delete** | Menghapus dengan menandai `deletedAt` — data tetap ada, tidak muncul di daftar |
| **Hard Delete / Permanent Delete** | Menghapus data dari database secara permanen (setelah 30 hari soft delete) |
| **Optimistic Update** | Memperbarui UI segera sebelum respons server — rollback jika gagal |
| **Uncomplete / Reopen** | Mengubah status dari completed kembali ke active |

## Teknis

| Istilah | Definisi |
|---|---|
| **DTO (Data Transfer Object)** | Objek yang digunakan untuk mentransfer data antar lapisan aplikasi |
| **Entity** | Objek domain yang dipetakan ke tabel database (TypeORM) |
| **React Query** | Library manajemen state server — caching, fetching, mutasi |
| **Zustand** | Library manajemen state client — UI state, filter |
