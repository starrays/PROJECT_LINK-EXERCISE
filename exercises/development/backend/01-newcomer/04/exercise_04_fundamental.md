# 🌐 FUNDAMENTAL – Modularisasi Server Node.js

Modularisasi adalah proses memecah kode menjadi bagian-bagian terpisah yang lebih kecil dan bertanggung jawab atas tugas spesifik. Ini adalah prinsip penting dalam membangun backend yang **terstruktur, scalable, dan mudah dikelola**.

---

## 🧱 Kenapa Modular?

| Tanpa Modular              | Dengan Modular                     |
|---------------------------|------------------------------------|
| Semua kode di satu file   | File terpisah sesuai tanggung jawab|
| Sulit dibaca dan debug     | Mudah dipahami dan di-review       |
| Rentan duplikasi kode      | Reusable & terstruktur             |
| Tidak scalable             | Bisa tumbuh jadi sistem besar      |

---

## 🧠 Prinsip Dasar Modularisasi di Node.js

### 🔹 1. Entry Point
File utama tempat server dijalankan: `server.js`

### 🔹 2. Routes
Menangani pemetaan URL ke handler: `routes/notes.js`

### 🔹 3. Controllers
Berisi logic utama atau "business logic": `controllers/notesController.js`

### 🔹 4. Utils / Helpers
Fungsi bantu seperti membaca file, validasi: `utils/file.js`

### 🔹 5. Data
Penyimpanan (sementara): `data/notes.json`

---

## 🔄 Contoh Struktur Modular

```
├── server.js
├── routes/
│   └── notes.js
├── controllers/
│   └── notesController.js
├── utils/
│   └── file.js
├── data/
│   └── notes.json
```

### Di dalam `routes/notes.js`
```js
const { getNotes, addNote } = require('../controllers/notesController');

function notesRouter(req, res) {
  if (req.url === '/notes' && req.method === 'GET') return getNotes(req, res);
  if (req.url === '/notes' && req.method === 'POST') return addNote(req, res);
}

module.exports = notesRouter;
```

### Di `server.js`
```js
const http = require('http');
const notesRouter = require('./routes/notes');

const server = http.createServer((req, res) => {
  notesRouter(req, res);
});

server.listen(3000);
```

---

## 📦 Module System di Node.js

Gunakan:
- `module.exports = functionName` → untuk ekspor
- `require('./file-path')` → untuk impor

Modularisasi = berpikir dalam potongan kecil yang dapat digunakan ulang dan diuji dengan mudah.

---

## 🧠 Tips Modularisasi
- Pisahkan file sesuai _fungsi_, bukan hanya panjang file
- Gunakan nama folder yang konsisten (`routes`, `controllers`, `utils`)
- Gunakan default parameter dan pengecekan error
- Dokumentasikan fungsi jika perlu (`README.md`, komentar)

---

## 🔗 Referensi
- [Node.js Modules](https://nodejs.org/api/modules.html)
- [Zellwk - Structure for Beginners](https://zellwk.com/blog/structure-node-js/)
- [Modular Node.js Project Pattern](https://dev.to/)

---

> "Semakin besar proyekmu, semakin penting struktur. Modular bukan tentang gaya—ini soal bertahan hidup di proyek nyata." 🧩

