# 🌐 FUNDAMENTAL – Routing Manual & File System di Node.js

Latihan ini mengajak kamu memahami bagaimana **routing sederhana** dan **pengelolaan data via file lokal** bisa menjadi dasar sistem backend tanpa database.

---

## 🔀 Apa Itu Routing?

**Routing** adalah proses menangani permintaan HTTP berdasarkan URL dan method-nya. Tujuannya agar server bisa membedakan:

- Permintaan `GET /users`
- vs `POST /users`
- vs `GET /users/123`

> 📬 Anggap routing seperti resepsionis yang menyaring setiap tamu (request) untuk diarahkan ke ruangan (handler) yang sesuai.

---

## 🧠 Routing Manual di Node.js (Tanpa Express)

Tanpa framework, kamu bisa menangani route seperti ini:

```js
if (req.url === '/users' && req.method === 'GET') {
  // logic baca file & kirim data
}
```

### Menangani JSON Body (POST):

```js
let body = '';
req.on('data', chunk => (body += chunk));
req.on('end', () => {
  const data = JSON.parse(body);
  // lanjut simpan ke file
});
```

---

## 📂 Apa Itu `fs` Module?

``** (file system)** adalah module bawaan Node.js untuk berinteraksi dengan file lokal seperti `.json`, `.txt`, dsb.

### Fungsi Umum `fs`:

| Fungsi              | Keterangan                       |
| ------------------- | -------------------------------- |
| `fs.readFileSync`   | Membaca isi file secara langsung |
| `fs.writeFileSync`  | Menimpa atau membuat file baru   |
| `fs.appendFileSync` | Menambahkan isi di akhir file    |
| `fs.existsSync`     | Mengecek apakah file tersedia    |

---

## 💡 Format Data JSON

File `data.json` umumnya berisi array:

```json
[
  {
    "id": 1,
    "name": "Raka",
    "hobby": "Backend"
  }
]
```

Saat menambahkan data:

1. Baca file → parse ke array → `.push()` data baru
2. Simpan kembali dengan `fs.writeFileSync`

---

## 🔧 Error Handling & Validasi

| Masalah Umum         | Solusi                                     |   |               |
| -------------------- | ------------------------------------------ | - | ------------- |
| File tidak ditemukan | Buat default `[]` jika `fs.readFile` error |   |               |
| Data tidak lengkap   | Cek \`!data.name                           |   | !data.hobby\` |
| JSON parse gagal     | Bungkus dengan `try { ... } catch`         |   |               |

---

## 🧪 Tips Modularisasi (Opsional)

- Pisahkan logic route handler ke fungsi terpisah
- Buat helper seperti `readData()`, `saveData()`
- Gunakan `path.join(__dirname, 'data.json')` untuk lokasi file yang aman lintas OS

---

## 🔗 Referensi Tambahan

- [Node.js File System](https://nodejs.org/api/fs.html)
- [MDN JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
- [HTTP Request Handling in Node.js](https://www.digitalocean.com/community/tutorials/)

---

> "Sebelum mengenal database besar, kamu harus mengerti bagaimana data hidup di file. Routing manual & fs adalah latihan logika backend paling murni." 📂💡

