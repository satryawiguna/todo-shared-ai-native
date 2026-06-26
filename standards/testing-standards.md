# Standar Pengujian (Testing Standards)

## Piramida Tes

```
        ┌──────┐
        │ E2E  │  10%  — Playwright (frontend), Supertest (backend)
        ├──────┤
        │ Inte │  20%  — API integration tests
        ├──────┤
        │ Unit │  70%  — Jest (services, hooks, utils)
        └──────┘
```

## Cakupan (Coverage)

- **Target:** ≥ 80% lines, ≥ 70% branches
- **Wajib di-test:** semua business logic, validasi, error handling
- **Tidak wajib:** getter/setter sederhana, config files

## Konvensi Penamaan

```typescript
describe('TodoService', () => {
  describe('create', () => {
    it('should create a todo with valid input', () => { ... });
    it('should throw error when title is empty', () => { ... });
    it('should throw error when title exceeds 200 characters', () => { ... });
  });

  describe('update', () => {
    it('should update an active todo', () => { ... });
    it('should throw error when updating a completed todo', () => { ... });
  });
});
```

## Aturan Mocking

| Komponen | Mock? | Keterangan |
|---|---|---|
| Repository/DB | ✅ Ya | Gunakan repository mock atau in-memory DB |
| External API | ✅ Ya | Gunakan MSW (frontend) atau nock (backend) |
| Service internal | ❌ Tidak | Test service asli dengan mock repository |
| Utility functions | ❌ Tidak | Test asli — pure functions |
| Config/Env | ✅ Ya | Gunakan test config |

## Frontend Spesifik

### Unit Test (Jest + React Testing Library)

```typescript
it('should display todo title', () => {
  render(<TodoCard todo={mockTodo} />);
  expect(screen.getByText('Beli susu')).toBeInTheDocument();
});
```

### Hook Test

```typescript
it('should return loading state initially', () => {
  const { result } = renderHook(() => useTodos());
  expect(result.current.isLoading).toBe(true);
});
```

### E2E Test (Playwright)

```typescript
test('user can create a todo', async ({ page }) => {
  await page.goto('/todos/create');
  await page.fill('[name="title"]', 'Beli susu');
  await page.click('button[type="submit"]');
  await expect(page.locator('.todo-card')).toContainText('Beli susu');
});
```

## Backend Spesifik

### Unit Test (Jest)

```typescript
it('should create a todo', async () => {
  const dto: CreateTodoDto = { title: 'Test', priority: 'high' };
  const result = await service.create(dto);
  expect(result.title).toBe('Test');
  expect(result.status).toBe('active');
});
```

### E2E Test (Supertest)

```typescript
it('POST /todos should create a todo', () => {
  return request(app.getHttpServer())
    .post('/todos')
    .send({ title: 'Test' })
    .expect(201)
    .expect(res => {
      expect(res.body.data.title).toBe('Test');
    });
});
```
