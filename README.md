# SisDigi UMKM - Backend Server

Ini adalah layanan backend untuk aplikasi **SisDigi UMKM**, sebuah platform inovatif yang memungkinkan pelaku UMKM untuk membuat website profesional hanya dengan deskripsi bahasa natural. Server ini bertanggung jawab atas otentikasi pengguna, logika bisnis, dan orkestrasi layanan AI dari AWS.

---

## 🚀 Fitur Utama

- **Otentikasi Pengguna:** Sistem registrasi dan login aman menggunakan JSON Web Tokens (JWT).
- **Orkestrasi AI:** Mengelola dan meracik *prompt* untuk dikirim ke **AWS Bedrock**, menerjemahkan bahasa natural menjadi kode HTML.
- **Manajemen Riwayat:** Menyimpan dan mengambil riwayat versi website untuk setiap pengguna dari database.
- **Manajemen Aset:** Menangani unggahan gambar (logo, produk) ke **AWS S3**.
- **Logika Publikasi:** Mempublikasikan dan menghapus website statis ke S3 Bucket yang terpisah.

---

## 🛠️ Arsitektur Teknologi

- **Framework:** Node.js, Express.js
- **Database:** MySQL
- **Layanan AWS:**
  - **AWS Bedrock:** Untuk akses ke LLM (Claude 3.5 Sonnet V1).
  - **AWS S3:** Untuk penyimpanan aset dan *static website hosting*.
- **Autentikasi:** JSON Web Tokens (JWT)
- **Dependencies Utama:** `mysql2`, `jsonwebtoken`, `multer`, `@aws-sdk/client-bedrock-runtime`, `@aws-sdk/client-s3`, `dotenv`.

---

## ⚙️ Instalasi & Konfigurasi Lokal

1.  **Clone Repository:**
    ```bash
    git clone [https://github.com/NAMA_USER_ANDA/sisdigi-umkm-backend.git](https://github.com/NAMA_USER_ANDA/sisdigi-umkm-backend.git)
    cd sisdigi-umkm-backend
    ```

2.  **Install Dependencies:**
    ```bash
    npm install
    ```

3.  **Setup Database:**
    - Pastikan Anda memiliki server MySQL yang berjalan (misalnya melalui Laragon).
    - Buat database baru (contoh: `simpel_ai_db`).
    - Jalankan skrip SQL di `database_schema.sql` (Anda bisa membuat file ini dan memasukkan perintah `CREATE TABLE` ke dalamnya) untuk membuat tabel `users` dan `generations`.
    

4.  **Jalankan Server:**
    ```bash
    node server.js
    ```
    Server akan berjalan di `http://localhost:3001`.

---

## 📄 API Endpoints

- `POST /api/auth/register`: Registrasi pengguna baru.
- `POST /api/auth/login`: Login pengguna.
- `GET /api/auth/me`: Mengambil data pengguna yang sedang login.
- `GET /api/generations`: Mengambil daftar riwayat website.
- `POST /api/generate`: Membuat website baru dari prompt.
- `POST /api/edit`: Mengedit website yang ada.
- `POST /api/publish/:id`: Mempublikasikan sebuah versi website.
- `DELETE /api/publish`: Menghapus publikasi website.
- `POST /api/upload`: (Protected) Mengunggah file gambar.
- `DELETE /api/generations/:id`: (Protected) Menghapus satu item riwayat project.
- `GET /api/generations/:id`: (Protected) Mengambil detail HTML dari satu riwayat.

---
*Proyek ini dikembangkan sebagai bagian dari AWS Online Hackathon 2025.*
