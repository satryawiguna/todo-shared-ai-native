# Panduan Dokumentasi

## Kapan Mendokumentasikan

| Situasi | Dokumentasi |
|---|---|
| Modul/package baru | ✅ Wajib — file README atau doc |
| API endpoint baru | ✅ Wajib — update Swagger + `api-contracts.md` |
| Aturan bisnis baru | ✅ Wajib — update `business/business-rules.md` |
| Perubahan arsitektur | ✅ Wajib — update `architecture/` |
| Bug fix sederhana | ❌ Tidak perlu — cukup commit message |
| Refactor internal | ❌ Tidak perlu — kecuali mengubah API publik |

## Format

- **Semua dokumentasi dalam Markdown** (`.md`)
- **Bahasa Indonesia** untuk konten
- **Kode dan istilah teknis** tetap dalam bahasa Inggris

## Struktur README (per repo)

```markdown
# Nama Proyek
Deskripsi satu kalimat

## 🚀 Mulai Cepat
Instruksi setup dan menjalankan dalam 3 langkah

## 📋 Prasyarat
Apa yang harus diinstal (Node.js, pnpm, Docker, dll.)

## 🛠️ Development
Cara menjalankan, test, lint, build

## 🐳 Docker
Cara menjalankan dengan Docker

## 📁 Struktur Proyek
Tree diagram folder utama

## 🧪 Testing
Cara menjalankan tes

## 📚 Dokumentasi
Link ke shared-context dan docs lokal
```

## Tempat Dokumentasi Disimpan

| Jenis Dokumentasi | Lokasi |
|---|---|
| Pengetahuan domain (produk, bisnis, arsitektur) | `todo-shared-ai-native-orchestration/` |
| Dokumentasi kode (API, komponen) | `/docs/` di masing-masing repo |
| Inline documentation | JSDoc / komentar di kode |
| AI context (instruksi, prompt, agent) | `.github/`, `.claude/`, `.cursor/` |
