# 🌐 FUNDAMENTAL – Intro to HTTP & API

Latihan ini membahas konsep paling dasar dalam backend modern: bagaimana data dikirim, diterima, dan diproses lewat protokol HTTP.

---

## 🧠 Apa Itu HTTP?

**HTTP (Hypertext Transfer Protocol)** adalah protokol komunikasi standar yang digunakan web browser dan server untuk saling bertukar data.

Setiap kali kamu:

- Membuka halaman website
- Login ke aplikasi
- Submit form

... kamu sedang menggunakan HTTP.

### Struktur HTTP

| Komponen | Deskripsi                                    |
| -------- | -------------------------------------------- |
| Request  | Permintaan yang dikirim client ke server     |
| Response | Balasan dari server untuk client             |
| Method   | Jenis aksi yang diminta (`GET`, `POST`, dll) |
| Header   | Metadata (format, status, izin, dll)         |
| Body     | Isi data yang dikirim (biasanya JSON)        |

---

## 🧩 Apa Itu API?

**API (Application Programming Interface)** adalah jembatan komunikasi antar aplikasi. Dalam konteks web, API berfungsi agar frontend bisa meminta/mengirim data ke backend melalui endpoint tertentu.

> 🔁 Analogi: API = pelayan restoran. Kamu (client) minta makanan (data), dapur (server) menyiapkan, lalu pelayan (API) mengantarkan balik ke meja kamu.

---

## 🔧 HTTP Methods

| Method | Tujuan Umum        | Contoh                         |
| ------ | ------------------ | ------------------------------ |
| GET    | Mengambil data     | `GET /users`                   |
| POST   | Mengirim data baru | `POST /users` dengan JSON body |
| PUT    | Memperbarui data   | `PUT /users/123`               |
| DELETE | Menghapus data     | `DELETE /users/123`            |

---

## 📬 Contoh Request JSON

```json
POST /data HTTP/1.1
Content-Type: application/json

{
  "name": "Raka",
  "email": "raka@link.id"
}
```

Contoh Response:

```json
{
  "message": "Data berhasil diterima!"
}
```

---

## 🧪 Apa Itu Status Code?

Status code menunjukkan hasil dari permintaan HTTP.

| Kode | Arti         | Penjelasan Singkat               |
| ---- | ------------ | -------------------------------- |
| 200  | OK           | Permintaan berhasil              |
| 201  | Created      | Data baru berhasil dibuat        |
| 400  | Bad Request  | Format data salah / tidak valid  |
| 404  | Not Found    | Endpoint tidak ditemukan         |
| 500  | Server Error | Terjadi kesalahan di sisi server |

---

## 🔧 Node.js HTTP Module

Node.js punya module bawaan (`http`) untuk membuat server dasar:

```js
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/hello' && req.method === 'GET') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Hello World' }));
  }
});

server.listen(3000, () => {
  console.log('Server aktif di http://localhost:3000');
});
```

---

## 🔗 Referensi Belajar

- [MDN - HTTP Basics](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- [Node.js HTTP Module](https://nodejs.org/api/http.html)
- [Postman API Testing](https://learning.postman.com/)

---

> "Memahami API dan HTTP adalah dasar mutlak bagi backend developer — tanpa itu, kita cuma menebak, bukan membangun." 🌐⚙️

