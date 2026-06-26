# Permissions Matrix

## Role: Authenticated User

| Action              | Own Task | Others' Task |
|---------------------|----------|--------------|
| View task           | ✅       | ❌           |
| Create task         | ✅       | ❌           |
| Edit task           | ✅       | ❌           |
| Delete task         | ✅       | ❌           |
| Change task status  | ✅       | ❌           |

## Role: Unauthenticated

| Action         | Allowed |
|----------------|---------|
| Register       | ✅      |
| Login          | ✅      |
| Any other      | ❌      |
