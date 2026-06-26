# Matriks Izin (Permissions Matrix)

*Catatan: Untuk MVP, autentikasi belum diimplementasikan. Matriks ini disiapkan untuk fondasi v1.*

## Peran (Roles)

| Peran | Deskripsi |
|---|---|
| **Admin** | Akses penuh — dapat mengelola semua todo dan pengguna |
| **Member** | Pengguna biasa — mengelola todo milik sendiri |
| **Viewer** | Hanya melihat — tidak dapat membuat atau mengubah todo |

## Matriks Aksi per Peran

| Aksi | Admin | Member | Viewer | Anonymous (MVP) |
|---|---|---|---|---|
| **Lihat daftar todo** | ✅ Semua | ✅ Milik sendiri | ✅ Milik sendiri | ✅ Semua |
| **Lihat detail todo** | ✅ Semua | ✅ Milik sendiri | ✅ Milik sendiri | ✅ Semua |
| **Buat todo** | ✅ | ✅ | ❌ | ✅ |
| **Ubah todo** | ✅ Semua | ✅ Milik sendiri (jika active) | ❌ | ✅ Semua (jika active) |
| **Hapus todo** | ✅ Semua | ✅ Milik sendiri | ❌ | ✅ Semua |
| **Complete todo** | ✅ Semua | ✅ Milik sendiri | ❌ | ✅ Semua |
| **Arsip todo** | ✅ Semua | ✅ Milik sendiri | ❌ | ❌ (v1) |
| **Kelola pengguna** | ✅ | ❌ | ❌ | ❌ (v1) |

## Catatan MVP

Pada fase MVP, **semua operasi bersifat publik** — tidak ada autentikasi. Semua pengguna dapat melihat, membuat, mengubah, dan menghapus todo. Ini disederhanakan untuk fokus pada fungsionalitas inti.

Autentikasi akan ditambahkan pada **v1** dengan JWT dan middleware guard di Nest.js.
