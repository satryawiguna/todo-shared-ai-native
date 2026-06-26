# Template: Review Arsitektur

> **Cara menggunakan:** Copy template ini, berikan ke AI bersama dengan kode/dokumen yang ingin direview.

---

Bandingkan implementasi saat ini dengan dokumen arsitektur dan standar berikut:

1. `architecture/system-overview.md` — gambaran sistem
2. `architecture/api-contracts.md` — kontrak API
3. `architecture/bounded-contexts.md` — batasan bounded context
4. `standards/coding-standards.md` — standar coding
5. `standards/security-guidelines.md` — panduan keamanan

Identifikasi:

1. **Penyimpangan** — bagian kode yang tidak sesuai dengan arsitektur yang didokumentasikan
2. **Risiko** — potensi masalah performa, keamanan, atau skalabilitas
3. **Kesenjangan** — komponen arsitektur yang belum diimplementasikan
4. **Saran Perbaikan** — rekomendasi konkret untuk setiap temuan

Gunakan tingkat keparahan:
- **P0** — Kritis, harus diperbaiki sebelum production
- **P1** — Penting, harus diperbaiki dalam sprint ini
- **P2** — Nice-to-have, bisa ditunda

Output dalam format checklist Markdown.
