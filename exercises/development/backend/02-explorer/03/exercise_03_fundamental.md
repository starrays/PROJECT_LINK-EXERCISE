# 🌿 FUNDAMENTAL – Middleware & Error Handling

Middleware adalah salah satu kekuatan utama dari Express.js. Mereka memungkinkan kita menambahkan logika tambahan di antara request dan response — seperti logging, validasi, parsing, otentikasi, hingga error handler.

---

## ⚙️ Apa Itu Middleware?

Middleware adalah **fungsi yang dijalankan sebelum route handler dijalankan**. Bentuknya:

```js
(req, res, next) => {
  // do something
  next(); // lanjut ke middleware/route berikutnya
}
```

> 🔁 Anggap middleware seperti **checkpoint atau filter** yang dilalui setiap request.

---

## 🔎 Jenis Middleware

| Jenis            | Fungsi Utama                   |
| ---------------- | ------------------------------ |
| `express.json()` | Mem-parse body JSON            |
| Logger           | Cetak method & URL             |
| Validator        | Cek isi body sebelum diproses  |
| Custom Header    | Tambahkan metadata ke response |
| Error Handler    | Tangani error secara global    |

---

## 🧱 Contoh Middleware Logger

```js
app.use((req, res, next) => {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
  next();
});
```

---

## 🛡️ Middleware Validator

Contoh:

```js
function validateNote(req, res, next) {
  const { title, content } = req.body;
  if (!title || !content) {
    return res.status(400).json({ error: 'Title & content wajib diisi.' });
  }
  next();
}
```

---

## ❌ Global Error Handler

```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: 'Terjadi kesalahan di server.' });
});
```

> Letakkan di paling akhir setelah semua route.

---

## ❓ Fallback 404 Handler

```js
app.use((req, res) => {
  res.status(404).json({ error: 'Route tidak ditemukan' });
});
```

---

## 🔗 Referensi Tambahan

- [Express Middleware](https://expressjs.com/en/guide/using-middleware.html)
- [Error Handling Express](https://expressjs.com/en/guide/error-handling.html)
- [Clean Code Express Middleware](https://dev.to/)

---

> "Middleware bukan hanya pengatur jalur, tapi penjaga kualitas dan keandalan request kamu di backend." 🔍

