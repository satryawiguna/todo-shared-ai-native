# Git Workflow

## Strategi Branch

Menggunakan **Trunk-Based Development** yang disederhanakan:

```
main
  └── feat/nama-fitur        (feature branch)
  └── fix/deskripsi-bug      (bug fix branch)
  └── chore/deskripsi-tugas  (maintenance branch)
```

## Alur Kerja

1. **Buat branch dari `main`**
   ```bash
   git checkout -b feat/nama-fitur
   ```

2. **Commit dengan conventional commits** (lihat di bawah)

3. **Push branch & buat Pull Request**
   - Judul PR: deskripsi singkat dalam bahasa Indonesia
   - Deskripsi PR: apa yang diubah, mengapa, screenshots (jika UI)

4. **Review & merge ke `main`**
   - Minimal 1 approval (setelah v1)
   - Squash merge untuk riwayat yang bersih

## Conventional Commits

Format: `<type>(<scope>): <description>`

| Type | Kegunaan |
|---|---|
| `feat` | Fitur baru |
| `fix` | Perbaikan bug |
| `refactor` | Refaktor kode (tanpa perubahan fungsional) |
| `style` | Perubahan formatting (spasi, titik koma, dll.) |
| `docs` | Dokumentasi |
| `test` | Menambah/memperbaiki tes |
| `chore` | Maintenance (update dependency, config) |

Contoh:
```
feat(todo): tambahkan fitur soft delete dengan masa retensi 30 hari
fix(todo): perbaiki validasi judul kosong saat update
docs(api): perbarui kontrak API untuk endpoint filter
```

## Commit Message

- **Bahasa Indonesia** untuk deskripsi
- **Maksimal 72 karakter** di baris judul
- **Jelaskan WHY**, bukan hanya WHAT
- **Referensi issue** jika ada: `fix(todo): perbaiki validasi #42`

## Template PR

```markdown
## Deskripsi
<!-- Jelaskan apa yang diubah dan mengapa -->

## Tipe Perubahan
- [ ] feat (fitur baru)
- [ ] fix (perbaikan bug)
- [ ] refactor
- [ ] docs
- [ ] test
- [ ] chore

## Checklist
- [ ] Tes sudah ditambahkan/diperbarui
- [ ] Lint lulus
- [ ] Build lulus
- [ ] Dokumentasi diperbarui (jika perlu)
```
