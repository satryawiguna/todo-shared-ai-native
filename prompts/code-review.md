# Template: Review Kode

> **Cara menggunakan:** Copy template ini, ganti `[FILE/PR]` dengan file atau PR yang ingin direview, lalu berikan ke AI.

---

Review kode berikut: **[FILE/PR]**

Gunakan standar berikut sebagai acuan (baca dari **MCP server `todo-shared-context`**):

1. `standards/coding-standards.md` — TypeScript, struktur file, error handling
2. `standards/naming-conventions.md` — penamaan file, class, fungsi, variabel
3. `standards/security-guidelines.md` — validasi input, error handling, secrets
4. `standards/testing-standards.md` — cakupan tes, mocking rules

Periksa:

1. **Kebenaran** — apakah kode berfungsi sesuai spesifikasi?
2. **Keamanan** — apakah ada celah keamanan?
3. **Kualitas** — apakah kode bersih, readable, dan mengikuti konvensi?
4. **Performa** — apakah ada potensi bottleneck?
5. **Tes** — apakah ada tes yang memadai?

Gunakan tingkat keparahan:
- **P0** — Blocker, harus diperbaiki sebelum merge
- **P1** — Major, harus diperbaiki segera
- **P2** — Minor, saran perbaikan

Output dalam format checklist Markdown dengan kode yang relevan.
