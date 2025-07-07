# 🌳 FUNDAMENTAL – Integrasi SQLite & Node.js

Pada level Builder, kamu akan belajar menghubungkan REST API dengan database sungguhan (SQLite) agar data persistent dan siap produksi.

---

## 🗄️ Apa Itu SQLite?

**SQLite** adalah database ringan berbasis file, cocok untuk prototipe, aplikasi kecil, atau pembelajaran. Tidak butuh server terpisah, cukup satu file `.db`.

---

## 🔗 Integrasi Node.js & SQLite

- Gunakan package `sqlite3` atau ORM seperti `knex.js` untuk query SQL dari Node.js.
- Contoh koneksi dasar:

```js
const sqlite3 = require('sqlite3').verbose();
const db = new sqlite3.Database('./db/notes.db');
```

- Query SQL bisa dijalankan dengan `db.run()`, `db.get()`, `db.all()`.

---

## 🧱 Struktur Tabel & Migrasi

- Tabel `notes` minimal: `id` (INTEGER, PK, AUTOINCREMENT), `title` (TEXT), `content` (TEXT), `created_at` (DATETIME)
- Migrasi: proses membuat/ubah tabel secara otomatis saat app dijalankan.

---

## 🔄 Operasi CRUD Dasar

- **Create**: `INSERT INTO notes (title, content, created_at) VALUES (?, ?, ?)`
- **Read**: `SELECT * FROM notes` atau `SELECT * FROM notes WHERE id = ?`
- **Update**: `UPDATE notes SET title = ?, content = ? WHERE id = ?`
- **Delete**: `DELETE FROM notes WHERE id = ?`

---

## 🛡️ Validasi & Error Handling

- Selalu validasi input sebelum query (title/content tidak kosong)
- Tangani error DB: query gagal, data tidak ditemukan, dsb.
- Gunakan status code HTTP yang sesuai (`201`, `400`, `404`, `500`)

---

## 💡 Tips

- Pisahkan logic DB ke file/module terpisah (`db.js` atau `models/`)
- Gunakan async/await (dengan wrapper/promise) untuk query DB
- Backup file `.db` secara berkala

---

## 🔗 Referensi
- [SQLite Node.js](https://www.sqlitetutorial.net/sqlite-nodejs/)
- [Knex.js Guide](https://knexjs.org/)
- [MDN SQL](https://developer.mozilla.org/en-US/docs/Glossary/SQL)

---

> "Database bukan hanya tempat menyimpan data, tapi jantung aplikasi yang andal dan scalable." 