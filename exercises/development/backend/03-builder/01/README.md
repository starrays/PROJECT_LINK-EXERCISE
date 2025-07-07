# Exercise 01: REST API + SQLite Integration 🗄️

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌳 Builder  
> **Estimated Time**: 2–3 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Membuat REST API CRUD terhubung ke database SQLite
- Memahami migrasi schema dan query dasar SQL
- Mengelola data persistent (bukan hanya in-memory)
- Menangani error dan validasi input pada operasi database

---

## 📖 Studi Kasus

> Kamu adalah backend engineer yang membangun API catatan (notes) untuk aplikasi produktivitas. Kali ini, data harus disimpan di database SQLite agar lebih aman dan scalable.

---

## 🛠 Tools & Setup

```bash
mkdir exercise-01-sqlite-integration
cd exercise-01-sqlite-integration
npm init -y
npm install express sqlite3
```

Buat file `app.js` dan folder `db/` untuk database.

---

## 🔧 Tugas Utama

1. Setup database SQLite di folder `db/`
2. Buat tabel `notes` (id, title, content, created_at)
3. Implementasi endpoint CRUD:
   - `GET /notes` → Ambil semua catatan
   - `GET /notes/:id` → Ambil catatan by id
   - `POST /notes` → Tambah catatan baru
   - `PUT /notes/:id` → Update catatan
   - `DELETE /notes/:id` → Hapus catatan
4. Validasi input pada create/update
5. Error handling untuk query gagal atau data tidak ditemukan

---

## ✨ Bonus Challenge

- Migrasi otomatis jika tabel belum ada
- Endpoint search: `GET /notes?search=...`
- Tabel relasi sederhana: user-note (opsional)

---

## 📁 Struktur File

```
exercise-01-sqlite-integration/
├── app.js
├── db/
│   └── notes.db
├── README.md
├── fundamental.md
└── migration.sql (opsional)
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-01-sqlite-integration/
├── app.js
├── db/
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi
- [SQLite Node.js](https://www.sqlitetutorial.net/sqlite-nodejs/)
- [Express.js CRUD](https://expressjs.com/en/starter/basic-routing.html)
- [Knex.js Docs](https://knexjs.org/)
- [MDN SQL](https://developer.mozilla.org/en-US/docs/Glossary/SQL)

---

> "Database adalah fondasi aplikasi modern. Menguasai integrasi API dan DB = skill wajib backend developer." 