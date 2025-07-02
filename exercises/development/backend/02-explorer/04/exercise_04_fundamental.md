# 🌿 FUNDAMENTAL – Modularisasi & Simulasi Autentikasi

Latihan ini melanjutkan praktik REST API yang kamu pelajari, dengan menambahkan **struktur modular** dan **middleware autentikasi** yang mensimulasikan sistem API key sederhana.

---

## 🧩 Kenapa Modularisasi Penting?

Saat proyek bertambah besar, kita tidak bisa terus menulis semua kode di satu file (`index.js`). Modularisasi membantu kita:

- Memisahkan tanggung jawab kode
- Memudahkan pemeliharaan & debugging
- Menyusun folder berdasarkan logika bisnis (route, controller, utils, dsb.)

---

## 📁 Struktur Modular Express

```
├── index.js
├── routes/              ← Menangani endpoint dan rute
├── controllers/         ← Logic dari masing-masing route
├── middleware/          ← Fungsi interceptors (validasi, auth)
├── utils/               ← Bantuan logic tambahan / manipulasi
├── .env (optional)
```

> Kamu bisa membuat folder `models/`, `services/`, atau `config/` jika dibutuhkan.

---

## 🛡️ Simulasi Autentikasi: x-api-key

Dalam produksi, kita menggunakan **JWT** atau OAuth. Namun dalam latihan ini, kita akan:

- Memeriksa header: `x-api-key`
- Jika key tidak cocok (`12345`), balas `401 Unauthorized`
- Jika cocok, lanjut ke controller

Middleware `auth.js`:

```js
function checkApiKey(req, res, next) {
  const apiKey = req.headers['x-api-key'];
  if (apiKey !== '12345') {
    return res.status(401).json({ error: 'Unauthorized' });
  }
  next();
}
```

---

## ⚙️ Best Practice Modular

| Komponen     | Tanggung Jawab                                    |
| ------------ | ------------------------------------------------- |
| routes/      | Menangani URL dan arahkan ke controller           |
| controllers/ | Menjalankan logic utama (akses data, return JSON) |
| middleware/  | Validasi input, proteksi, logger, error handler   |
| utils/       | Fungsi bantu (generate ID, validasi format, dsb.) |

---

## 💬 Tips

- Simpan API key di `.env` untuk keamanan (optional dengan `dotenv`)
- Selalu gunakan `next(err)` untuk forward error ke error handler
- Gunakan struktur yang sama di semua latihan lanjutan

---

## 🔗 Referensi

- [Express Folder Structure](https://zellwk.com/blog/structure-node-js/)
- [Express Auth Middleware](https://expressjs.com/en/guide/using-middleware.html)
- [REST API Security Guide](https://www.freecodecamp.org/news/rest-api-security-best-practices/)

---

> "Modularisasi itu bukan gaya coding, tapi cara berpikir jangka panjang. Sekarang kamu bukan cuma membuat kode — kamu membangun fondasi sistem." 🧠

