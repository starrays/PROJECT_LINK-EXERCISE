# Exercise 01: Express Starter & Routing 🚀

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌿 Explorer\
> **Estimated Time**: 1 jam\
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Menginstal dan menjalankan Express.js
- Membuat server pertama dengan Express
- Menangani route dasar (`GET`, `POST`)
- Memahami struktur request dan response

---

## 📖 Studi Kasus

> Kamu adalah developer backend yang ditugaskan membuat API untuk menyambut pengguna dan menerima data nama. Ini adalah langkah awal sebelum membangun sistem REST API skala penuh.

---

## 🛠 Tools & Setup

```bash
mkdir exercise-01-express-intro
cd exercise-01-express-intro
npm init -y
npm install express
```

Buat file `index.js`

---

## 🔧 Tugas Utama

1. Jalankan server di port 3000
2. Buat route `GET /` → return JSON `{ message: "Welcome to Express" }`
3. Buat route `POST /hello` → menerima JSON `{ name: "Raka" }`, dan kembalikan `{ message: "Hello, Raka!" }`
4. Gunakan `express.json()` sebagai middleware

---

## ✨ Bonus Challenge

- Tambahkan route `GET /ping?name=...` untuk menyapa via query param
- Tambahkan `nodemon` untuk auto-reload saat coding
- Tambahkan response time logger sederhana

---

## 📁 Struktur File

```
exercise-01-express-intro/
├── index.js
├── README.md
└── fundamental.md
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-01-express-intro/
├── index.js
└── REFLECTION.md
```

---

## 🔗 Referensi

- [Express.js Getting Started](https://expressjs.com/en/starter/hello-world.html)
- [MDN Query Params](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams)

---

> "Langkah kecil pertama dengan Express akan membuka gerbang besar menuju API production-ready."

