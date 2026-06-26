# Diagram ERD (Entity Relationship Diagram)

```mermaid
erDiagram
    todos {
        char id PK "UUID"
        varchar title "1-200 chars, NOT NULL"
        text description "NULLABLE, max 1000"
        enum status "active | completed"
        enum priority "low | medium | high"
        timestamp created_at "auto"
        timestamp updated_at "auto"
        timestamp deleted_at "NULLABLE — soft delete"
    }
```

## Catatan

- `deleted_at` digunakan untuk soft delete — todo yang dihapus tetap ada di database
- `status` default: `active`
- `priority` default: `medium`
- `id` menggunakan UUID v4 untuk keamanan (tidak mudah ditebak)
