# Todo Project — Basis Pengetahuan AI-Native

## Tentang Repositori Ini

Repositori ini adalah **basis pengetahuan dokumentasi murni** untuk proyek Todo. Tidak ada kode di sini — hanya dokumentasi Markdown yang dapat dikonsumsi oleh alat AI (GitHub Copilot, Claude Code, Cursor, Windsurf) saat bekerja di repositori frontend atau backend.

## Struktur

```
todo-shared-ai-native-orchestration/
├── product/          # Visi, roadmap, kebutuhan, user stories, kriteria acceptance
├── business/         # Aturan bisnis, alur kerja, glosarium, matriks izin
├── architecture/     # Desain sistem, bounded context, kontrak API, alur event
├── standards/        # Konvensi coding, penamaan, git, keamanan, pengujian
├── diagrams/         # ERD, diagram C4, diagram sequence (Mermaid)
├── prompts/          # Template prompt AI yang dapat digunakan kembali
└── docs/             # Dokumentasi tambahan
```

## Cara Menggunakan

1. Clone repositori ini bersamaan dengan repositori frontend/backend
2. Alat AI akan secara otomatis membaca `AGENTS.md` dan menavigasi ke dokumen yang relevan
3. Atau, tambahkan sebagai Git submodule di repositori kode:
   ```bash
   git submodule add <url> docs/shared-context
   ```

## Stack Teknologi

| Komponen | Teknologi |
|---|---|
| Frontend | Next.js 15, TanStack React Query, Zustand, Axios, Tailwind CSS |
| Backend | Nest.js, TypeORM, MySQL |
| Package Manager | pnpm |
| Deployment | Docker |
