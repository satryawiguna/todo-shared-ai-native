# Alur Kerja (Workflows)

## WF-01: Alur Membuat Todo

```
Pengguna klik "Buat Todo Baru"
  → Form muncul (judul, deskripsi, prioritas)
  → Pengguna isi form
  → Klik "Simpan"
  → Validasi frontend (Zod)
  → POST /todos (backend)
  → Validasi backend (class-validator)
  → Simpan ke database
  → Response 201 dengan todo baru
  → React Query invalidasi cache
  → Kembali ke daftar todo (todo baru muncul)
```

## WF-02: Alur Mengubah Todo

```
Pengguna klik todo → halaman detail
  → Klik "Edit"
  → Form terisi data existing
  → Pengguna ubah data
  → Klik "Simpan"
  → Validasi frontend
  → Backend cek: apakah todo completed?
    → Jika completed: tolak (error 422)
    → Jika active: lanjutkan
  → PUT /todos/:id
  → Simpan ke database
  → Response 200 dengan todo yang diupdate
  → React Query invalidasi cache
  → Kembali ke detail (data terbaru)
```

## WF-03: Alur Menghapus Todo

```
Pengguna klik "Hapus" pada todo
  → Muncul dialog konfirmasi
  → Jika batal: tidak ada aksi
  → Jika konfirmasi:
    → Optimistic update (todo hilang dari UI segera)
    → DELETE /todos/:id (backend)
    → Backend set deletedAt = now()
    → Response 200
    → React Query invalidasi cache
    → Jika error: rollback optimistic update + tampilkan error
```

## WF-04: Alur Menandai Todo Selesai

```
Pengguna centang checkbox pada todo
  → Optimistic update (status UI berubah ke completed)
  → PUT /todos/:id { status: "completed" }
  → Backend validasi
  → Simpan ke database
  → Response 200
  → React Query invalidasi cache
  → Jika error: rollback + tampilkan error
```

## WF-05: State Machine Todo

```
State: draft (tidak digunakan di MVP)
  ↓
State: active (default saat dibuat)
  → Bisa diedit: ✅
  → Bisa dihapus: ✅
  → Bisa di-complete: ✅
  ↓ (setelah dicentang)
State: completed
  → Bisa diedit: ❌ (BR-01)
  → Bisa dihapus: ✅
  → Bisa di-uncomplete: ✅
  ↓ (setelah diarsipkan - fitur v1)
State: archived
  → Bisa diedit: ❌
  → Bisa dihapus: ✅ (permanen)
  → Bisa di-restore: ✅ (kembali ke active)
```
