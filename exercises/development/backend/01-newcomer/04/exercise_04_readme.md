# Exercise 04: Modular Server Structure 🧩

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌱 Newcomer\
> **Estimated Time**: 2–3 jam\
> **Last Updated**: Juni 2025

---

## 🎯 Tujuan Pembelajaran

- Menyusun struktur kode backend menjadi lebih modular dan maintainable
- Memecah file berdasarkan tanggung jawab (handler, utils, data)
- Menangani routing secara lebih terorganisir
- Membangun mental model arsitektur backend skala kecil

---

## 📖 Studi Kasus

> Kamu bekerja di tim kecil yang mengembangkan API internal. Tim frontend mengeluhkan bahwa file `server.js` terlalu panjang dan tidak terbaca. Tugasmu adalah merapikan kode menjadi struktur modular sambil tetap menjaga fungsionalitas.

---

## 🛠 Tools & Setup

| Alat    | Deskripsi                     |
| ------- | ----------------------------- |
| Node.js | Runtime backend utama         |
| fs      | File system untuk simpan data |
| VS Code | Editor kode                   |

### Struktur Awal

```bash
mkdir exercise-04-modular-server
cd exercise-04-modular-server
npm init -y
```

---

## 🔧 Tugas Utama

Bangun ulang API sederhana dengan struktur berikut:

```
GET    /notes      → Tampilkan daftar catatan
POST   /notes      → Tambah catatan baru
```

### Struktur Modular:

```
exercise-04-modular-server/
├── server.js              ← Entry point
├── routes/
│   └── notes.js           ← Routing handler
├── controllers/
│   └── notesController.js ← Logic bisnis tiap endpoint
├── utils/
│   └── file.js            ← Baca/tulis file JSON
├── data/
│   └── notes.json         ← Penyimpanan data
```

### Fitur Wajib:

- Gunakan `module.exports` & `require()`
- Pisahkan route, logic, dan utils
- Tambahkan validasi & status code sesuai
- Gunakan `fs` untuk simpan/load file

---

## ✨ Bonus Challenge

- Tambahkan `DELETE /notes/:id` untuk hapus berdasarkan ID
- Gunakan helper untuk generate ID (`Date.now()` atau counter)
- Tambahkan logger per request ke `log.txt`

---

## ✅ Submission

```
submissions/backend/[username]/exercise-04-modular-server/
├── server.js
├── routes/...
├── controllers/...
└── REFLECTION.md
```

---

## 🔗 Referensi

- [Node.js Modules](https://nodejs.org/api/modules.html)
- [Project Structure for Beginners](https://zellwk.com/blog/structure-node-js/)
- [fs Module](https://nodejs.org/api/fs.html)

---

> "Modularitas adalah kunci keberlanjutan dalam proyek backend. Semakin rapi struktur, semakin mudah tim bertumbuh bersama."

