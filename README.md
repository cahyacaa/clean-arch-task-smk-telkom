# Tugasss: Implementasi Aplikasi Manajemen User dengan Clean Architecture di Golang

## Deskripsi
Buatlah sebuah aplikasi manajemen user sederhana dengan menerapkan prinsip **Clean Architecture** ala Uncle Bob di Golang. Aplikasi harus menyediakan endpoint REST untuk:

- **Mendaftarkan user baru**
- **Login (catat waktu login)**
- **Mengambil profil user yang sedang login (jangan sampai user lain bisa melihat informasi user lainnya)**
- **Logout (catat waktu logout)**

Gunakan **Gin Gonic** sebagai framework HTTP dan terapkan pemisahan lapisan (layer) sesuai dengan Clean Architecture, yaitu:

- **Domain (Entities)**
- **Use Case (Business Logic)**
- **Interface Adapters (Controller / Handler & Presenter)**
- **Infrastructure (Repository Implementation & Framework Integration)**

Gunakan repository berbasis penyimpanan in-memory untuk menyimpan data user dan authentication.

Gunakan JWT (JSON Web Token) untuk menyimpan informasi yang dibutuhkan saat login

## Spesifikasi Teknis

### 1. Domain Layer (Entities)
- Buat struct `User` yang memuat:
  - `ID` (int)
  - `Name` (string)
  - `Email` (string)
  - `CreatedAt` (time.Time)
 
- Buat struct `Authentication` yang memuat:
  - `ID` (int)
  - `UserID` (int)
  - `Password` (string)
  - `Token`  (string)
  - `LoginAt` (time.Time)
  - `LogoutAt` (time.Time)

### 2. Struktur Folder
```
project/
├── cmd/
│   └── main.go
├── internal/
│   ├── domain/
│   │   └── user.go
│   │   └── authentication.go
│   ├── usecase/
│   │   └── user.go
│   │   └── authentication.go
│   └── presenter/
│       └── user_presenter_in.go
|       └── user_presenter_out.go
│       └── authentication_presenter_in.go
|       └── authentication_presenter_out.go
├── infrastructure/
│   └── in_memory_user_repo.go
├── delivery/
│   └── http/
│       └── user_controller.go
└── go.mod
```
