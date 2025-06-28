# Exercise 01: Intro to HTTP & API Basics 🌐

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌱 Newcomer\
> **Estimated Time**: 1–2 jam\
> **Last Updated**: Juni 2025

---

## 🎯 Tujuan Pembelajaran

- Memahami cara kerja HTTP dan API dalam komunikasi client-server
- Mampu membuat server sederhana menggunakan `http` core module dari Node.js
- Merespons permintaan GET dan POST dengan data JSON
- Mengelola request, response, status code, dan headers

---

## 📖 Studi Kasus

> Kamu adalah backend developer pemula yang sedang belajar membangun REST API. Dalam latihan ini, kamu diminta untuk membuat server lokal yang dapat:
>
> - Menyapa pengguna melalui endpoint `/hello`
> - Menerima data melalui endpoint `/data` dan menampilkannya di terminal

---

## 🛠 Tools & Setup

| Alat     | Keterangan                       |
| -------- | -------------------------------- |
| Node.js  | Runtime JavaScript untuk backend |
| VS Code  | Text editor                      |
| Postman  | REST Client untuk test API       |
| Terminal | Menjalankan server & debug log   |

### Struktur Awal

```bash
mkdir exercise-01-intro-api
cd exercise-01-intro-api
npm init -y
touch server.js
```

---

## 🔧 Tugas Utama

1. Buat server dengan module `http`
2. Endpoint `GET /hello` → `{ "message": "Hello World" }`
3. Endpoint `POST /data` → Menerima JSON dari client, tampilkan isinya di terminal
4. Gunakan header `Content-Type: application/json`
5. Tambahkan status code (`200`, `201`, `400`, dll.) sesuai hasil

---

## ✨ Bonus Challenge

- Tambahkan endpoint `GET /data` yang membaca file `data.json`
- Simpan hasil `POST` ke file `data.json` menggunakan `fs`
- Validasi body agar berisi `{ name, email }`

---

## 📁 Struktur File Disarankan

```
exercise-01-intro-api/
├── server.js
├── data.json           ← (opsional bonus)
├── README.md
└── fundamental.md
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-01-intro-api/
├── server.js
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi

- [Node.js HTTP module](https://nodejs.org/api/http.html)
- [MDN - HTTP Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- [Postman Docs](https://learning.postman.com/)

---

> "REST API adalah bahasa universal antar aplikasi. Ini langkah pertama untuk berkomunikasi di dunia digital."

