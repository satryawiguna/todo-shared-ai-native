# Panduan Keamanan (Security Guidelines)

## OWASP Top 10 — Mitigasi

### 1. Validasi Input (A03:2021 — Injection)

- **Semua input divalidasi** — frontend (Zod) dan backend (class-validator)
- **Whitelist, bukan blacklist** — tentukan apa yang diizinkan, bukan apa yang dilarang
- **TypeORM parameterized queries** — mencegah SQL injection secara otomatis
- **Sanitasi HTML** — jika menerima rich text, gunakan DOMPurify

### 2. Keamanan HTTP Headers

- **Helmet** diaktifkan di Nest.js — set security headers otomatis
- **CSP (Content Security Policy)** — konfigurasi di Next.js
- **CORS** — hanya izinkan origin yang diketahui (dari environment variable)

### 3. Rate Limiting

- **Global rate limit** — 100 request per menit per IP
- **Stricter limits** untuk endpoint sensitif (auth — v1)
- Gunakan `@nestjs/throttler`

### 4. Environment Variables

- **Tidak ada secrets di kode** — semua credentials di `.env`
- **Validasi env dengan Zod** — startup validation, fail fast
- **`.env` di `.gitignore`** — tidak pernah di-commit
- Gunakan `.env.example` sebagai template

### 5. Dependencies

- **Regular audit** — `pnpm audit` secara berkala
- **Minimalkan dependencies** — evaluasi setiap library baru
- **Lock file di-commit** — `pnpm-lock.yaml` harus ada di repo

### 6. Error Handling

- **Jangan expose stack traces** — di production, exception filter harus menyembunyikan detail
- **Error messages generik untuk user** — "Terjadi kesalahan" bukan "Connection refused at 127.0.0.1:3306"
- **Log detail error di server** — untuk debugging internal

### 7. Data Protection

- **Soft delete, bukan hard delete** — data tidak benar-benar hilang selama 30 hari
- **HTTPS only** — di production, semua komunikasi via HTTPS
- **No sensitive data in URL** — gunakan POST body, bukan query params untuk data sensitif

## Checklist Keamanan per Endpoint

- [ ] Input divalidasi (wajib/opsional, panjang, format)
- [ ] CORS diaktifkan dengan origin yang benar
- [ ] Rate limiting diterapkan
- [ ] Helmet security headers aktif
- [ ] Error tidak membocorkan informasi internal
- [ ] Response time reasonable (tidak ada slow query tanpa index)
