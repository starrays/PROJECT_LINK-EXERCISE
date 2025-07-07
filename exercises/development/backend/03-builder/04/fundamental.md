# 🌳 FUNDAMENTAL – MVC Structure in Backend

Arsitektur **MVC (Model-View-Controller)** adalah pola desain yang memisahkan aplikasi menjadi tiga bagian utama agar lebih terstruktur, scalable, dan mudah di-maintain.

---

## 🏗️ Apa Itu MVC?

- **Model**: Mengelola data dan query ke database
- **View**: (Pada API, biasanya tidak digunakan, tapi bisa untuk response format)
- **Controller**: Logic bisnis, validasi, dan mengatur alur data
- **Router**: (Tambahan di Express) Menangani endpoint dan arahkan ke controller

---

## 🧱 Struktur Folder MVC di Node.js

```
project/
├── app.js
├── models/
├── controllers/
├── routes/
├── db/
├── utils/
```

- **models/**: Query DB, relasi, schema
- **controllers/**: Logic endpoint, validasi, error handling
- **routes/**: Definisi endpoint dan middleware
- **utils/**: Helper (format response, error, dsb.)
- **db/**: File database atau migrasi

---

## 💡 Manfaat MVC

- Kode lebih modular dan mudah di-maintain
- Kolaborasi tim lebih efisien
- Mudah testing/unit test
- Siap untuk scaling dan penambahan fitur

---

## 🔧 Contoh Routing ke Controller

```js
// routes/notes.js
const express = require('express');
const router = express.Router();
const notesController = require('../controllers/notesController');

router.get('/', notesController.getAllNotes);
router.post('/', notesController.createNote);
// dst.

module.exports = router;
```

---

## 🔗 Referensi
- [MVC Pattern](https://developer.mozilla.org/en-US/docs/Glossary/MVC)
- [Express.js Project Structure](https://zellwk.com/blog/structure-node-js/)
- [Knex.js Docs](https://knexjs.org/)

---

> "MVC bukan sekadar pola, tapi budaya kerja tim backend modern." 