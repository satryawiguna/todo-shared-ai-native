# Standar Coding

## TypeScript

- **Strict mode wajib** — `"strict": true` di `tsconfig.json`
- **Tanpa `any`** — gunakan `unknown` jika tipe benar-benar tidak diketahui
- **Pilih `interface` daripada `type`** untuk objek — kecuali jika butuh union/intersection
- **Named exports only** — hindari `export default`
- **Gunakan `const` assertions** (`as const`) untuk literal types

```typescript
// ✅ Benar
interface TodoItem {
  id: string;
  title: string;
}
export { TodoItem };

// ❌ Salah
export default interface TodoItem { ... }
const data: any = fetchData();
```

## Struktur File

- **Satu class/komponen per file** — kecuali untuk tipe kecil terkait
- **Co-locate tipe spesifik** — tipe yang hanya digunakan oleh satu komponen diletakkan di file yang sama
- **Barrel exports** — gunakan `index.ts` untuk mengekspor ulang dari folder

## Fungsi

- **Fungsi kecil & fokus** — maksimal 50 baris
- **Satu tanggung jawab** — satu fungsi melakukan satu hal
- **Pure functions lebih disukai** — hindari side effect jika memungkinkan
- **Gunakan arrow functions untuk callback** — konsistensi

## Impor

Urutan impor (gunakan ESLint `import/order`):

1. Node built-in (`path`, `fs`)
2. External packages (`@nestjs/common`, `react`)
3. Internal absolute (`@/components/TodoCard`)
4. Internal relative (`./utils`)
5. Types (`import type { ... }`)

## Error Handling

- **Jangan swallow error** — selalu log atau propagate
- **Gunakan custom exception classes** — jangan throw string
- **Frontend**: gunakan error boundaries + toast untuk user-facing errors
- **Backend**: gunakan exception filters Nest.js

```typescript
// ✅ Benar (Backend)
throw new BusinessRuleViolationException('Todo yang sudah selesai tidak dapat diubah');

// ❌ Salah
throw new Error('gagal');
```

## Komentar

- **Komentari WHY, bukan WHAT** — kode menjelaskan apa, komentar menjelaskan mengapa
- **TODO**: `// TODO(nama): deskripsi` — harus ada nama dan deskripsi
- **JSDoc untuk fungsi publik** — minimal satu baris deskripsi
