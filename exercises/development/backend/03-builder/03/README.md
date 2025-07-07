# Exercise 03: Relational Data & Joins 🔗

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌳 Builder  
> **Estimated Time**: 2–3 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Membuat dan mengelola relasi antar tabel di database (1:N, M:N)
- Menggunakan query join untuk mengambil data relasi
- Membuat endpoint dengan nested response
- Optimasi query dan struktur data

---

## 📖 Studi Kasus

> Kamu membangun API untuk aplikasi catatan yang kini mendukung multi-user. Setiap user bisa punya banyak notes. Kamu perlu membuat relasi user-note dan endpoint yang bisa mengambil data user beserta catatannya.

---

## 🛠 Tools & Setup

```bash
npm install sqlite3
# atau gunakan knex.js
```

- Tambahkan tabel `users` dan relasi ke `notes`

---

## 🔧 Tugas Utama

1. Buat tabel `users` (id, name, email)
2. Tambahkan kolom `user_id` di tabel `notes`
3. Implementasi endpoint:
   - `GET /users` → Ambil semua user
   - `GET /users/:id/notes` → Ambil semua notes milik user tertentu
   - `POST /users` → Tambah user baru
   - `POST /notes` → Tambah note untuk user tertentu
4. Gunakan query join untuk nested response
5. Validasi dan error handling relasi

---

## ✨ Bonus Challenge

- Implementasi relasi M:N (misal: notes bisa punya banyak tag)
- Endpoint filter: `GET /notes?user_id=...`
- Optimasi query (index, limit, dsb.)

---

## 📁 Struktur File

```
exercise-03-relational-joins/
├── app.js
├── db/
├── README.md
├── fundamental.md
└── migration.sql (opsional)
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-03-relational-joins/
├── app.js
├── db/
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi
- [SQLite Foreign Key](https://www.sqlitetutorial.net/sqlite-foreign-key/)
- [SQL JOIN](https://www.sqlitetutorial.net/sqlite-inner-join/)
- [Knex.js Relations](https://knexjs.org/guide/relations.html)

---

> "Relasi data adalah kunci aplikasi multi-user dan scalable. Kuasai join, kuasai backend!" 