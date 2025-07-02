# Exercise 03: Middleware & Error Handler 🧱

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌿 Explorer  
> **Estimated Time**: 2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Mengenal dan membuat middleware di Express
- Membuat logger sederhana dan middleware validasi
- Menangani error secara global dengan middleware error handler
- Membuat fallback `404 Not Found` handler

---

## 📖 Studi Kasus

> Dalam sistem backend nyata, kita sering butuh mencatat request, memeriksa validasi, dan menangani error secara konsisten. Latihan ini mensimulasikan pembuatan "kerangka middleware" untuk API catatan.

---

## 🛠 Tools & Setup

```bash
mkdir exercise-03-middleware-error
cd exercise-03-middleware-error
npm init -y
npm install express
```

---

## 🔧 Tugas Utama

1. Buat file `index.js` dengan setup Express + `express.json()`
2. Buat array `notes[]` sebagai data in-memory (seperti sebelumnya)
3. Tambahkan middleware:
   - Logger: cetak method, url, dan timestamp setiap request
   - Validator: cek `POST /notes` harus berisi `title`, `content`
4. Implementasi route:
   - `GET /notes`
   - `POST /notes`
5. Tambahkan **middleware error handler** global (`app.use((err, req, res, next) => {...})`)
6. Tambahkan handler `404` di akhir route

---

## ✨ Bonus Challenge

- Tambahkan `x-api-version` di semua response header via middleware
- Middleware time tracker untuk menghitung waktu eksekusi tiap request
- Simulasikan error untuk dites ke error handler global

---

## 📁 Struktur File
```
exercise-03-middleware-error/
├── index.js
├── README.md
└── fundamental.md
```

---

## ✅ Submission
```
submissions/backend/[username]/exercise-03-middleware-error/
├── index.js
└── REFLECTION.md
```

---

## 🔗 Referensi
- [Express Middleware Guide](https://expressjs.com/en/guide/using-middleware.html)
- [Error Handling Best Practices](https://expressjs.com/en/guide/error-handling.html)
- [MDN HTTP Status Reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---

> "Middleware itu seperti filter dan pengawas. Mereka memastikan request diproses secara benar, aman, dan efisien."

