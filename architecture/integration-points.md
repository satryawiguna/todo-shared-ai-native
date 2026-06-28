# Titik Integrasi (Integration Points)

*Untuk MVP, tidak ada integrasi eksternal. Dokumen ini disiapkan untuk fondasi v1+.*

## Layanan Eksternal (v1+)

| Layanan | Tujuan | Status |
|---|---|---|
| **Auth0 / Supabase Auth** | Autentikasi pengguna (register, login, JWT) | Rencana v1 |
| **SendGrid / Resend** | Email notifikasi (verifikasi, pengingat deadline) | Rencana v2 |
| **Datadog / Sentry** | Monitoring & error tracking | Rencana v1 |

## Konfigurasi Environment

Semua konfigurasi koneksi eksternal disimpan di environment variables:

```env
# Environment
NODE_ENV=local              # local | development | production
PORT=5000                   # local:5000, dev:5001, prod:5002

# Database
DB_HOST=localhost
DB_PORT=3306                # 3307 untuk Docker dev, 3308 untuk prod
DB_USERNAME=root
DB_PASSWORD=secret
DB_DATABASE=todo_db

# CORS (multiple origins, comma-separated)
CORS_ORIGINS=http://localhost:3000,http://localhost:3001

# Auth (v1)
JWT_SECRET=your-jwt-secret
JWT_EXPIRATION=1h

# Email (v2)
SENDGRID_API_KEY=your-api-key
EMAIL_FROM=noreply@todoapp.com
```

## Fallback Behavior

| Layanan | Jika Gagal |
|---|---|
| Database | Kembalikan 500 — jangan lanjutkan tanpa database |
| Auth (v1) | Kembalikan 401 — endpoint terproteksi tidak bisa diakses |
| Email (v2) | Log error — jangan blokir operasi utama (non-critical) |
| Monitoring | Log ke console — jangan ganggu operasi utama |
