# Konvensi Penamaan (Naming Conventions)

## File & Folder

| Kategori | Konvensi | Contoh |
|---|---|---|
| Folder | `kebab-case` | `todo-list/`, `api-services/` |
| File TypeScript/React | `kebab-case.ts` / `.tsx` | `todo-card.tsx`, `create-todo.dto.ts` |
| File test | `*.spec.ts` (unit), `*.e2e-spec.ts` | `todo.service.spec.ts` |
| File konfigurasi | `kebab-case.config.ts` | `database.config.ts` |

## Kode

| Kategori | Konvensi | Contoh |
|---|---|---|
| Class / Interface / Type | `PascalCase` | `TodoService`, `CreateTodoDto` |
| Interface | `PascalCase` (tanpa prefix `I`) | `ApiResponse<T>` |
| Enum | `PascalCase` | `TodoStatus`, `Priority` |
| Enum members | `UPPER_SNAKE_CASE` atau `camelCase` | `COMPLETED` atau `completed` |
| Fungsi / Method | `camelCase` | `createTodo()`, `findAllTodos()` |
| Variabel | `camelCase` | `todoList`, `isLoading` |
| Konstanta global | `UPPER_SNAKE_CASE` | `MAX_TITLE_LENGTH`, `API_BASE_URL` |
| Private field | `camelCase` (tanpa `_` prefix) | `private readonly todoRepo` |
| React Component | `PascalCase` (sesuai nama file) | `TodoCard`, `TodoForm` |
| React Hook | `use` prefix + `camelCase` | `useTodos`, `useCreateTodo` |
| Zustand Store | `camelCase` + `Store` suffix | `todoFilterStore`, `uiStore` |

## Nest.js Spesifik

| Kategori | Konvensi | Contoh |
|---|---|---|
| Module | `PascalCase` + `Module` | `TodoModule` |
| Controller | `PascalCase` + `Controller` | `TodoController` |
| Service | `PascalCase` + `Service` | `TodoService` |
| Entity | `PascalCase` (tabel: plural `snake_case`) | `Todo` → tabel `todos` |
| DTO | `PascalCase` + `Dto` | `CreateTodoDto`, `UpdateTodoDto` |
| Guard | `PascalCase` + `Guard` | `JwtAuthGuard` |
| Pipe | `PascalCase` + `Pipe` | `ValidationPipe` |

## Database

| Kategori | Konvensi | Contoh |
|---|---|---|
| Tabel | Plural `snake_case` | `todos`, `users` |
| Kolom | `snake_case` | `created_at`, `updated_at` |
| Primary Key | `id` (UUID) | `id CHAR(36)` |
| Foreign Key | `[tabel_singular]_id` | `user_id` |
| Indeks | `idx_[tabel]_[kolom]` | `idx_todos_status` |
