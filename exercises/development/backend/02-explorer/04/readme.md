# Exercise 04: Modular Express API + Simulasi Auth 🧩

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌿 Explorer\
> **Estimated Time**: 2.5–3 jam\
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Membangun struktur Express API secara modular dan scalable
- Memecah kode menjadi folder `routes/`, `controllers/`, dan `utils/`
- Menambahkan simulasi otentikasi sederhana dengan `req.headers`
- Menggunakan `middleware` untuk proteksi route

---

## 📖 Studi Kasus

> Kamu membuat API catatan (notes) untuk tim internal. Beberapa route hanya bisa diakses jika header `x-api-key` sesuai. Kamu perlu membuat struktur project Express yang bersih dan aman, sekaligus scalable untuk dikembangkan ke tahap selanjutnya.

---

## 🛠 Tools & Setup

```bash
mkdir exercise-04-modular-auth-sim
cd exercise-04-modular-auth-sim
npm init -y
npm install express
```

---

## 🔧 Tugas Utama

1. Buat struktur modular:

```
├── index.js
├── routes/
│   └── notes.js
├── controllers/
│   └── notesController.js
├── middleware/
│   └── auth.js
├── utils/
│   └── notesData.js (in-memory array)
```

2. Endpoint yang harus dibuat:

- `GET /notes` → Public
- `POST /notes` → Hanya jika header `x-api-key: 12345`
- `DELETE /notes/:id` → Proteksi + validasi

3. Tambahkan middleware:

- Logger (boleh pakai sebelumnya)
- Auth (periksa `x-api-key`)

---

## 🧠 Logika Simulasi Auth

```js
function checkApiKey(req, res, next) {
  const key = req.headers['x-api-key'];
  if (key !== '12345') {
    return res.status(401).json({ error: 'Unauthorized' });
  }
  next();
}
```

---

## ✨ Bonus Challenge

- Pindahkan config `API_KEY` ke `.env` file
- Modularisasi error handler
- Gunakan controller terpisah untuk validasi

---

## ✅ Submission

```
submissions/backend/[username]/exercise-04-modular-auth-sim/
├── index.js
├── routes/...
├── controllers/...
├── middleware/...
├── utils/...
└── REFLECTION.md
```

---

## 🔗 Referensi

- [Express Routing (Advanced)](https://expressjs.com/en/guide/routing.html)
- [Middleware Design Patterns](https://expressjs.com/en/guide/using-middleware.html)
- [Clean Express App Structure](https://zellwk.com/blog/structure-node-js/)

---

> "Modularisasi bukan sekadar struktur — ia adalah jembatan menuju API produksi yang aman dan mudah di-maintain."

