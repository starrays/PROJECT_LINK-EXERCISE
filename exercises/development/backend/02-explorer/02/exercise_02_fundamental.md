# 🌿 FUNDAMENTAL – CRUD API & Input Validation

Latihan ini membahas praktik inti dalam backend modern: **membangun API CRUD** dan **memastikan input yang dikirim oleh pengguna valid dan aman** sebelum diproses.

---

## ⚙️ Apa Itu CRUD?

CRUD adalah singkatan dari:

- **C**reate → membuat data baru (POST)
- **R**ead → membaca data (GET)
- **U**pdate → memperbarui data (PUT / PATCH)
- **D**elete → menghapus data (DELETE)

Ini adalah pola paling umum yang digunakan oleh hampir semua API modern.

---

## 🧱 Struktur Data Sementara (In-memory)

Kita akan menyimpan data sementara di array seperti:

```js
const notes = [
  { id: 1, title: 'Belajar', content: 'Express dasar' }
];
```

---

## 🔄 Operasi CRUD Dasar

### `GET /notes`

- Mengirim semua note

### `POST /notes`

- Menambahkan note baru
- Wajib validasi: `title` dan `content` ada dan bukan string kosong

### `PUT /notes/:id`

- Update note tertentu
- Cek apakah ID ditemukan → update atau kirim error `404`

### `DELETE /notes/:id`

- Hapus note tertentu berdasarkan ID

---

## 🛡️ Validasi Input

Validasi digunakan untuk:

- Mencegah data kosong atau salah format
- Meningkatkan keamanan
- Memberi feedback error yang jelas

Contoh validasi manual:

```js
if (!title || typeof title !== 'string') {
  return res.status(400).json({ error: 'Title tidak valid' });
}
```

> Validasi input = filter keamanan dan kualitas data sebelum masuk ke logika utama.

---

## 🔧 Status Code Penting

| Status | Makna                       |
| ------ | --------------------------- |
| 200    | OK (berhasil)               |
| 201    | Created (data baru)         |
| 400    | Bad Request (invalid input) |
| 404    | Not Found                   |

---

## 🎁 Tips

- Gunakan `Date.now()` untuk ID unik sederhana
- Ekstrak validasi ke fungsi terpisah
- Gunakan middleware untuk reusable validation (lanjutan)

---

## 🔗 Referensi

- [Express Routing](https://expressjs.com/en/guide/routing.html)
- [RESTful Patterns](https://restfulapi.net/rest-put-vs-post/)
- [Node.js Validasi Manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

---

> "Sebelum menyimpan data, pastikan kamu tahu apa yang kamu simpan. Validasi itu seperti filter sebelum masuk dapur produksi." 🍽️

