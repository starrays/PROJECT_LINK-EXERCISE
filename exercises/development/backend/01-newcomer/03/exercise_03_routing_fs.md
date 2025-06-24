# Exercise 03: Routing & File System Basics 🗂️

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌱 Newcomer\
> **Estimated Time**: 1.5–2.5 jam\
> **Last Updated**: Juni 2025

---

## 🎯 Tujuan Pembelajaran

- Memahami cara kerja **routing** (pemilahan endpoint) secara manual
- Menggunakan module `fs` untuk membaca & menulis file lokal
- Membuat server yang menyimpan & menampilkan data dari file
- Mengelola response status code dan header JSON

---

## 📖 Studi Kasus

> Kamu membangun server kecil untuk menyimpan dan membaca daftar pengguna. Setiap pengguna memiliki nama dan hobi. Data akan disimpan di file `data.json`. Server ini akan memiliki endpoint:
>
> - `GET /users` → Tampilkan daftar pengguna dari file
> - `POST /users` → Terima JSON dan simpan ke file

---

## 🛠 Tools & Setup

| Alat    | Deskripsi                              |
| ------- | -------------------------------------- |
| Node.js | Runtime JavaScript                     |
| fs      | Modul bawaan Node.js untuk file I/O    |
| curl    | Untuk test `POST` atau gunakan Postman |

### Struktur Awal

```bash
mkdir exercise-03-routing-fs
cd exercise-03-routing-fs
touch server.js data.json
```

Inisialisasi `data.json`:

```json
[]
```

---

## 🔧 Tugas Utama

1. Buat server HTTP (manual, tidak pakai Express)
2. Endpoint `GET /users`
   - Baca isi `data.json`
   - Kirim sebagai JSON response
3. Endpoint `POST /users`
   - Terima JSON `{ name, hobby }`
   - Tambahkan ke `data.json` (append), kirim respons `201 Created`
4. Gunakan header `Content-Type: application/json`
5. Tambahkan validasi sederhana jika data tidak lengkap

---

## ✨ Bonus Challenge

- Tambahkan ID unik ke setiap data (`Date.now()` atau counter sederhana)
- Tambahkan endpoint `GET /users/:id` (opsional)
- Tambahkan log request sederhana ke `log.txt`

---

## 📁 Struktur File Disarankan

```
exercise-03-routing-fs/
├── server.js
├── data.json
├── log.txt         ← (optional bonus)
├── README.md
└── fundamental.md
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-03-routing-fs/
├── server.js
├── data.json
└── REFLECTION.md
```

---

## 🔗 Referensi

- [Node.js fs module](https://nodejs.org/api/fs.html)
- [MDN JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---

> "Routing & filesystem adalah fondasi sebelum masuk framework. Menguasainya = memahami aliran data secara penuh."

