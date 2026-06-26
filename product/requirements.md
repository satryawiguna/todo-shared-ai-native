# Kebutuhan (Requirements)

## Kebutuhan Fungsional

### FR-01: Manajemen Todo
- FR-01.1: Pengguna dapat membuat todo baru dengan judul dan deskripsi opsional
- FR-01.2: Pengguna dapat melihat daftar semua todo
- FR-01.3: Pengguna dapat melihat detail satu todo
- FR-01.4: Pengguna dapat mengubah todo (judul, deskripsi, status, prioritas)
- FR-01.5: Pengguna dapat menghapus todo (soft delete)

### FR-02: Filter & Pencarian
- FR-02.1: Filter berdasarkan status (semua, aktif, selesai)
- FR-02.2: Filter berdasarkan prioritas (rendah, sedang, tinggi)
- FR-02.3: Pencarian berdasarkan judul (case-insensitive, partial match)

### FR-03: Paginasi
- FR-03.1: Daftar todo ditampilkan dengan paginasi (default 10 per halaman)
- FR-03.2: Pengguna dapat memilih jumlah item per halaman (10, 20, 50)

### FR-04: Validasi
- FR-04.1: Judul wajib diisi, minimal 1 karakter, maksimal 200 karakter
- FR-04.2: Deskripsi opsional, maksimal 1000 karakter
- FR-04.3: Status harus salah satu dari: `active`, `completed`
- FR-04.4: Prioritas harus salah satu dari: `low`, `medium`, `high`

## Kebutuhan Non-Fungsional

### NFR-01: Performa
- NFR-01.1: API response time < 200ms untuk operasi CRUD tunggal
- NFR-01.2: Frontend first contentful paint < 1.5 detik
- NFR-01.3: Mendukung hingga 10.000 todo per pengguna tanpa degradasi

### NFR-02: Keandalan
- NFR-02.1: Uptime API 99.5%
- NFR-02.2: Soft delete — data tidak benar-benar hilang selama 30 hari
- NFR-02.3: Validasi ketat di frontend DAN backend

### NFR-03: Keamanan
- NFR-03.1: Semua input divalidasi dan disanitasi
- NFR-03.2: CORS dikonfigurasi dengan benar
- NFR-03.3: Rate limiting untuk mencegah abuse
- NFR-03.4: HTTP security headers (Helmet)
