# C4 Level 2: Container Diagram

```mermaid
C4Container
    title Container Diagram — Todo App

    Person(user, "Pengguna", "Browser")

    System_Boundary(todoBoundary, "Todo App") {
        Container(webApp, "Next.js 15", "React, RQ, Zustand", "Frontend — menampilkan UI")
        Container(api, "Nest.js", "TypeORM", "Backend API — logika bisnis")
        ContainerDb(db, "MySQL 8", "Database", "Menyimpan data todo")
    }

    Rel(user, webApp, "Akses halaman", "HTTPS :3000")
    Rel(webApp, api, "REST API calls", "HTTP :3001")
    Rel(api, db, "Query & mutasi", "TCP :3306")
    
    UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```
