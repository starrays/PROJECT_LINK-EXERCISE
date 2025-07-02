# Exercise 02: CRUD API + Input Validation 🛠️

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌿 Explorer  
> **Estimated Time**: 1.5–2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Membangun REST API dengan metode `GET`, `POST`, `PUT`, `DELETE`
- Menyimpan data secara sementara (dalam array / memori)
- Melakukan validasi input sederhana
- Menangani status code dan error message secara konsisten

---

## 📖 Studi Kasus

> Kamu akan membangun API sederhana untuk mengelola daftar catatan (notes). Setiap note memiliki `id`, `title`, dan `content`. Semua data disimpan dalam array untuk sementara.

---

## 🛠 Tools & Setup

```bash
mkdir exercise-02-crud-validation
cd exercise-02-crud-validation
npm init -y
npm install express
```

---

## 🔧 Tugas Utama

Buat file `index.js` dengan fitur:

1. **`GET /notes`** → Tampilkan semua catatan
2. **`POST /notes`**
   - Input: `{ title, content }`
   - Tambahkan `id` (gunakan `Date.now()` atau counter)
   - Validasi wajib: `title` dan `content` tidak boleh kosong
3. **`PUT /notes/:id`** → Update note berdasarkan `id`
4. **`DELETE /notes/:id`** → Hapus note berdasarkan `id`

---

## 🧪 Contoh Data
```json
{
  "title": "Belajar REST API",
  "content": "Hari ini belajar CRUD pakai Express."
}
```

---

## ✨ Bonus Challenge

- Tambahkan middleware validasi reusable
- Buat helper fungsi `findNoteIndexById()`
- Tambahkan pencarian note via query param: `GET /notes?search=belajar`

---

## 📁 Struktur File
```
exercise-02-crud-validation/
├── index.js
├── README.md
└── fundamental.md
```

---

## ✅ Submission
```
submissions/backend/[username]/exercise-02-crud-validation/
├── index.js
└── REFLECTION.md
```

---

## 🔗 Referensi
- [Express.js Routing](https://expressjs.com/en/guide/routing.html)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [RESTful API Design](https://restfulapi.net/)

---

> "CRUD adalah jantung dari API. Validasi input adalah pintunya."

