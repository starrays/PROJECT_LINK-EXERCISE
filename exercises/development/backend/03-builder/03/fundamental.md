# 🌳 FUNDAMENTAL – Relational Data & SQL Joins

Aplikasi modern hampir selalu membutuhkan relasi antar data. Di level Builder, kamu akan belajar membangun dan meng-query relasi tersebut di database.

---

## 🔗 Apa Itu Relasi Database?

- **Relasi 1:N**: Satu user punya banyak notes (user_id di notes)
- **Relasi M:N**: Banyak notes bisa punya banyak tag (tabel pivot: note_tags)
- **Foreign Key**: Kolom yang menghubungkan dua tabel

---

## 🧱 Membuat Relasi di SQLite

- Tambahkan kolom `user_id` di tabel `notes`
- Aktifkan foreign key constraint di SQLite
- Contoh:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT,
  email TEXT
);

CREATE TABLE notes (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  user_id INTEGER,
  title TEXT,
  content TEXT,
  FOREIGN KEY(user_id) REFERENCES users(id)
);
```

---

## 🔄 Query Join

- **Inner Join**: Mengambil data dari dua tabel yang saling berelasi

```sql
SELECT users.name, notes.title
FROM users
JOIN notes ON users.id = notes.user_id;
```

- Nested response: Gabungkan data user dan notes dalam satu response JSON

---

## 🛡️ Validasi & Error Handling

- Pastikan user_id valid sebelum insert note
- Tangani error jika relasi tidak ditemukan

---

## 💡 Tips

- Gunakan index pada kolom foreign key untuk optimasi
- Pisahkan logic relasi ke model/helper terpisah
- Cek referensi integrity sebelum delete user

---

## 🔗 Referensi
- [SQLite Foreign Key](https://www.sqlitetutorial.net/sqlite-foreign-key/)
- [SQL JOIN](https://www.sqlitetutorial.net/sqlite-inner-join/)
- [Knex.js Relations](https://knexjs.org/guide/relations.html)

---

> "Relasi dan join = pondasi aplikasi multi-user dan data kompleks." 