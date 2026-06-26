# Aturan Bisnis (Business Rules)

## BR-01: Todo yang Selesai Tidak Dapat Diedit

Todo dengan status `completed` bersifat **immutable** — tidak dapat diubah judul, deskripsi, maupun prioritasnya. Ini mencegah perubahan tidak disengaja pada riwayat tugas yang sudah selesai.

**Pengecualian:** Status dapat diubah kembali ke `active` (uncomplete).

## BR-02: Judul Todo Wajib & Terbatas

- Judul **wajib** diisi (tidak boleh kosong)
- Panjang judul **minimal 1 karakter, maksimal 200 karakter**
- Spasi di awal dan akhir akan di-trim otomatis

## BR-03: Deskripsi Opsional

- Deskripsi bersifat opsional
- Jika diisi, maksimal **1000 karakter**

## BR-04: Soft Delete 30 Hari

- Todo yang dihapus tidak benar-benar hilang — data disimpan dengan flag `deletedAt`
- Todo yang dihapus **tidak muncul** di daftar normal
- Data akan dibersihkan permanen setelah **30 hari** (batch job / cron)
- Ini memungkinkan fitur "restore" di masa depan

## BR-05: Status Todo

Status todo mengikuti state machine berikut:

```
draft → active → completed → archived
  ↑        ↑         ↑
  └────────┴─────────┘ (bisa kembali ke active)
```

- `active`: Todo sedang dikerjakan (default saat dibuat)
- `completed`: Todo sudah selesai (immutable — lihat BR-01)
- `archived`: Todo diarsipkan (tidak muncul di daftar default)

## BR-06: Prioritas Todo

- `low`: Prioritas rendah — dikerjakan jika ada waktu luang
- `medium`: Prioritas sedang — default untuk todo baru
- `high`: Prioritas tinggi — harus dikerjakan segera

## BR-07: Tidak Ada Duplikasi Judul dalam Waktu Dekat

*(Aturan opsional untuk v1)* — Pengguna tidak dapat membuat todo dengan judul yang sama persis dalam waktu 5 menit terakhir. Ini mencegah duplikasi tidak sengaja.
