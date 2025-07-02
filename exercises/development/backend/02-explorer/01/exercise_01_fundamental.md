# 🌱 FUNDAMENTAL – Express.js & Routing Dasar

Latihan ini mengenalkan kamu pada Express.js, framework backend minimalis yang sangat populer untuk membangun REST API. Kita mulai dari hal-hal paling dasar: membuat server, membuat route, dan memahami bagaimana data mengalir dalam permintaan dan balasan (request-response).

---

## ⚙️ Apa Itu Express.js?

**Express** adalah framework web backend untuk Node.js yang membuat proses pembuatan server dan route menjadi lebih ringkas dan mudah.

> Analogi: Express = jalur cepat membuat backend. Tanpa perlu tulis ulang logika HTTP dasar.

---

## 📦 Instalasi

```bash
npm install express
```

Gunakan `require('express')` untuk menggunakannya di file JavaScript.

---

## 🚀 Membuat Server Pertama

```js
const express = require('express');
const app = express();
const PORT = 3000;

app.use(express.json()); // middleware untuk parsing JSON

app.get('/', (req, res) => {
  res.json({ message: 'Welcome to Express' });
});

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

---

## 🧭 Mengenal Route

**Route** adalah titik masuk (endpoint) yang menangani permintaan user.

```js
app.get('/hello', (req, res) => { ... });
app.post('/user', (req, res) => { ... });
```

### Method Populer:

| Method | Tujuan         |
| ------ | -------------- |
| GET    | Mengambil data |
| POST   | Mengirim data  |
| PUT    | Update data    |
| DELETE | Hapus data     |

---

## 📥 Mengambil Data dari Request

### Body JSON (POST):

```js
app.post('/hello', (req, res) => {
  const { name } = req.body;
  res.json({ message: `Hello, ${name}!` });
});
```

### Query Parameter:

```js
app.get('/ping', (req, res) => {
  const name = req.query.name;
  res.json({ message: `Hi ${name || 'there'}!` });
});
```

---

## 💡 Middleware & express.json()

Middleware adalah fungsi yang berjalan sebelum route handler dipanggil. Contoh yang umum:

```js
app.use(express.json()); // mengubah body JSON jadi object JavaScript
```

---

## 🔄 Debug Otomatis dengan Nodemon (opsional)

```bash
npm install --save-dev nodemon
npx nodemon index.js
```

---

## 🔗 Referensi Lanjut

- [Express.js Guide](https://expressjs.com/)
- [REST API Overview](https://restfulapi.net/)
- [Middleware Explained](https://expressjs.com/en/guide/using-middleware.html)

---

> "Pahami request dan response seperti kamu memahami percakapan: siapa bicara, apa isi pesannya, dan bagaimana merespons dengan tepat." 🧠

