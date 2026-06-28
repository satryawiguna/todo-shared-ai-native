# Template: Perencanaan Fitur

> **Cara menggunakan:** Copy template ini, ganti `[FITUR]` dengan nama fitur yang ingin direncanakan, lalu berikan ke AI (Copilot/Chat).

---

Baca dokumen berikut dari **MCP server `todo-shared-context`** (GitHub: `satryawiguna/todo-shared-ai-native`):

1. `product/requirements.md` — kebutuhan fungsional & non-fungsional
2. `product/user-stories.md` — user stories terkait
3. `product/acceptance-criteria.md` — kriteria acceptance
4. `business/business-rules.md` — aturan bisnis yang relevan
5. `architecture/api-contracts.md` — kontrak API yang terpengaruh
6. `architecture/system-overview.md` — gambaran sistem

Berdasarkan dokumen di atas, buat rencana implementasi untuk fitur: **[FITUR]**

Output yang diharapkan:

1. **Ringkasan Fitur** — 2-3 kalimat deskripsi
2. **File yang Terpengaruh** — daftar file yang perlu dibuat/diubah
   - Frontend Dashboard: `todo-app-ai-native-orchestration/apps/dashboard`
   - Frontend Landing Page: `todo-app-ai-native-orchestration/apps/landing-page`
   - Backend: `todo-api-ai-native-orchestration/`
3. **Perubahan Model Data** — kolom/tabel baru (jika ada)
4. **Perubahan API** — endpoint baru atau modifikasi
5. **Komponen UI** — komponen React baru yang dibutuhkan
6. **Rencana Tes** — unit test, integration test, E2E test yang perlu ditambahkan
7. **Estimasi Story Points** — 1, 2, 3, 5, atau 8

Format output dalam Markdown terstruktur.
