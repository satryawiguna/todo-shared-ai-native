# API Contracts

## Base URL

```
Production : https://api.todo-app.com/v1
Development: http://localhost:3001/v1
```

## Standard Response Format

### Success
```json
{
  "success": true,
  "data": { },
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 100
  }
}
```

### Error (RFC 7807)
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Title is required",
    "details": []
  }
}
```

## Endpoints Summary

### Auth
| Method | Path             | Description            |
|--------|------------------|------------------------|
| POST   | /auth/register   | Registrasi user baru   |
| POST   | /auth/login      | Login, return JWT      |
| POST   | /auth/refresh    | Refresh access token   |
| POST   | /auth/logout     | Invalidate token       |

### Tasks
| Method | Path               | Description              |
|--------|--------------------|--------------------------|
| GET    | /tasks             | List tasks (filter + pagination) |
| POST   | /tasks             | Create task              |
| GET    | /tasks/:id         | Get task by ID           |
| PATCH  | /tasks/:id         | Update task              |
| DELETE | /tasks/:id         | Soft delete task         |
| PATCH  | /tasks/:id/status  | Change task status       |

## Auth Header
```
Authorization: ******
```
