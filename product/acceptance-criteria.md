# Kriteria Acceptance (Acceptance Criteria)

## US-01: Melihat Daftar Todo

**Given** ada beberapa todo di database  
**When** pengguna membuka halaman daftar todo  
**Then** semua todo ditampilkan dengan paginasi (10 per halaman)  
**And** setiap todo menampilkan judul, status, dan prioritas  
**And** halaman menampilkan total jumlah todo

---

## US-02: Membuat Todo Baru

**Given** pengguna berada di halaman buat todo  
**When** pengguna mengisi judul "Beli susu" dan memilih prioritas "Tinggi" lalu klik Simpan  
**Then** todo baru muncul di daftar dengan status "Aktif"  
**And** muncul notifikasi sukses  

**Given** pengguna berada di halaman buat todo  
**When** pengguna mengosongkan judul dan klik Simpan  
**Then** muncul pesan error "Judul wajib diisi"  
**And** todo tidak tersimpan  

**Given** pengguna berada di halaman buat todo  
**When** pengguna mengisi judul lebih dari 200 karakter dan klik Simpan  
**Then** muncul pesan error "Judul maksimal 200 karakter"  
**And** todo tidak tersimpan

---

## US-03: Melihat Detail Todo

**Given** ada todo dengan id tertentu  
**When** pengguna membuka halaman detail todo tersebut  
**Then** semua informasi todo ditampilkan (judul, deskripsi, status, prioritas, tanggal dibuat)  

**Given** todo dengan id tidak ada  
**When** pengguna membuka halaman detail todo tersebut  
**Then** halaman menampilkan pesan "Todo tidak ditemukan"

---

## US-04: Mengubah Todo

**Given** ada todo yang belum selesai  
**When** pengguna mengubah judul dan klik Simpan  
**Then** todo diperbarui dengan judul baru  
**And** muncul notifikasi sukses  

**Given** ada todo yang sudah selesai (status = completed)  
**When** pengguna mencoba mengubah todo  
**Then** muncul pesan error "Todo yang sudah selesai tidak dapat diubah"

---

## US-05: Menghapus Todo

**Given** ada todo di daftar  
**When** pengguna mengklik Hapus pada todo tersebut  
**Then** muncul konfirmasi "Apakah Anda yakin?"  
**And** jika dikonfirmasi, todo dihapus dari daftar  
**And** muncul notifikasi sukses

---

## US-09: Menandai Todo Selesai

**Given** ada todo dengan status "Aktif"  
**When** pengguna mencentang checkbox selesai  
**Then** status todo berubah menjadi "Selesai"  
**And** tampilan todo berubah (teks dicoret, warna berubah)
