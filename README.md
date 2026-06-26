# Todo App — Shared Context

Repositori ini adalah **single source of truth** untuk seluruh konteks lintas-tim pada project Todo App.
Dibaca oleh semua AI tools (GitHub Copilot, Claude, Cursor, Windsurf) via referensi di masing-masing repo.

## Struktur

```
todo-shared-ai-native/
├── product/          # Visi, requirements, user stories
├── business/         # Business rules, glossary, permissions
├── architecture/     # System design, API contracts
├── standards/        # Git workflow, security guidelines
├── diagrams/         # ERD, C4, sequence diagrams (coming soon)
└── prompts/          # Reusable AI prompts lintas-repo
```

## Cara Menggunakan

| AI Tool | Cara Menggunakan |
|---------|-----------------|
| **GitHub Copilot** | Direferensikan via `.github/copilot-instructions.md` di masing-masing repo |
| **Claude** | Attach folder ini sebagai project knowledge |
| **Cursor** | Tambahkan path folder ini di Cursor Settings > Docs |
| **Windsurf** | Referensikan via `WINDSURF.md` di masing-masing repo |

## Repo Terkait

- `todo-frontend` — Next.js 14 + TypeScript + Tailwind + shadcn/ui
- `todo-api` — Node.js + TypeScript + Express + MySQL

## Aturan Kontribusi

- Semua perubahan pada dokumen ini harus melalui Pull Request
- Perubahan pada `architecture/api-contracts.md` wajib dikomunikasikan ke kedua repo
- Gunakan Conventional Commits untuk commit message (lihat `standards/git-workflow.md`)
