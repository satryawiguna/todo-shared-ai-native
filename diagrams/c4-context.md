# C4 Level 1: System Context

```mermaid
C4Context
    title System Context — Todo App

    Person(user, "Pengguna", "Mengelola daftar tugas melalui browser")
    
    System(todoSystem, "Todo App", "Aplikasi manajemen tugas sederhana")
    
    System_Ext(authSystem, "Auth Provider (v1)", "Autentikasi pengguna")
    System_Ext(emailSystem, "Email Service (v2)", "Pengiriman notifikasi email")
    
    Rel(user, todoSystem, "Melihat, membuat, mengubah, menghapus todo", "HTTPS")
    Rel(todoSystem, authSystem, "Verifikasi token JWT", "HTTPS (v1)")
    Rel(todoSystem, emailSystem, "Kirim notifikasi", "SMTP/API (v2)")
    
    UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```
