# Todo Project — Basis Pengetahuan Bersama

Repositori ini berisi pengetahuan domain untuk aplikasi Todo. Ini adalah **sumber kebenaran tunggal** untuk keputusan produk, bisnis, arsitektur, dan standar — yang dikonsumsi oleh alat AI (GitHub Copilot, Claude Code, Cursor, Windsurf) saat bekerja di repositori frontend atau backend.

## Cara AI Menggunakan Repositori Ini

Saat mengerjakan repositori frontend monorepo (`todo-app-ai-native-orchestration` — terdiri dari 2 aplikasi: **Dashboard** dan **Landing Page**) atau backend (`todo-api-ai-native-orchestration`), SELALU baca basis pengetahuan ini terlebih dahulu:

| Jika ingin tahu... | Baca... |
|---|---|
| **Apa yang dibangun & mengapa** | `product/` — visi, kebutuhan, user stories, kriteria acceptance |
| **Aturan domain** | `business/` — aturan bisnis, alur kerja, glosarium, matriks izin |
| **Desain sistem** | `architecture/` — gambaran sistem, bounded context, kontrak API, alur event |
| **Cara membangun** | `standards/` — coding, penamaan, git, keamanan, pengujian, dokumentasi |
| **Referensi visual** | `diagrams/` — ERD, diagram C4, diagram sequence |
| **Template prompt AI** | `prompts/` — template untuk perencanaan fitur, review arsitektur, review kode |

## Konvensi Utama

- **Baca dokumen yang relevan SEBELUM membuat kode apa pun**
- Jika aturan bisnis bertentangan dengan pemahamanmu, IKUTI dokumen
- Jika arsitektur atau kontrak API tidak jelas, TANYA — jangan berasumsi
- Perbarui dokumen saat keputusan berubah (ini adalah dokumen hidup)

## Dukungan Multi-Tool

| Alat AI | Cara Menggunakan |
|---|---|
| **GitHub Copilot** | Membaca `AGENTS.md` secara native |
| **Claude Code** | Membaca `CLAUDE.md` yang mengimpor `@AGENTS.md` |
| **Cursor** | Membaca `AGENTS.md` secara native + `.cursor/rules/shared-context.mdc` |
| **Windsurf** | Membaca `.windsurfrules` |
