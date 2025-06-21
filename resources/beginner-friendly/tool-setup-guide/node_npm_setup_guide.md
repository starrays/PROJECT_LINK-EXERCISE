# 📦 Node.js & NPM: Panduan Dasar untuk Pemula

**Node.js** dan **NPM** adalah dua alat yang penting bagi siapa pun yang ingin belajar web development modern, terutama di sisi JavaScript. Bahkan jika kamu hanya mengerjakan frontend, kamu tetap akan bersentuhan dengan keduanya.

---

## ⚡ Apa Itu Node.js?
- **Node.js** adalah runtime JavaScript di luar browser.
- Memungkinkan kamu menjalankan kode JavaScript di komputer langsung (bukan di browser).
- Diperlukan untuk menjalankan tool seperti bundler (Vite/Webpack), framework (React), dan CLI tools modern.

### 🔁 Perumpamaan:
> Browser adalah "mesin JavaScript dalam browser", Node.js adalah "mesin JavaScript tanpa browser" — langsung di sistem operasi.

---

## 📦 Apa Itu NPM?
- **NPM (Node Package Manager)** adalah tempat mengelola library dan tools berbasis JavaScript.
- Kamu bisa menginstal ribuan package dengan 1 baris perintah.
- NPM otomatis terinstall saat kamu install Node.js

---

## 🔧 Cara Install Node.js dan NPM

### 1. Download Node.js:
- Situs resmi: [https://nodejs.org](https://nodejs.org)
- Pilih versi **LTS (Long-Term Support)** untuk stabilitas

### 2. Cek versi setelah install:
```bash
node -v
npm -v
```

---

## 🧪 Contoh Penggunaan NPM

### 1. Inisialisasi proyek:
```bash
npm init -y
```
Ini akan membuat file `package.json`

### 2. Install package:
```bash
npm install [nama-library]
```
Contoh: `npm install axios`

### 3. Jalankan perintah script:
Tambahkan ke `package.json`:
```json
"scripts": {
  "start": "node index.js"
}
```
Lalu jalankan:
```bash
npm start
```

---

## 📁 Struktur Proyek Node Dasar
```
my-app/
├── index.js
├── package.json
├── node_modules/ ← otomatis saat install package
└── .gitignore     ← sebaiknya abaikan node_modules di Git
```

---

## 🌍 Alternatif Node + Package Manager
| Tool         | Keterangan                                      |
|--------------|--------------------------------------------------|
| **Yarn**     | Alternatif lebih cepat dan ringan dari NPM       |
| **Bun**      | Runtime + package manager modern super cepat     |
| **PNPM**     | Paket sharing antar proyek, hemat disk space     |

> Untuk pemula, cukup fokus ke NPM dulu.

---

## 🔗 Referensi Tambahan
- [Node.js Docs](https://nodejs.org/en/docs)
- [NPM Docs](https://docs.npmjs.com/)
- [FreeCodeCamp – Node Intro](https://www.freecodecamp.org/news/what-is-node-js/)
- [Node.js Playground](https://replit.com/@languages/nodejs)

---

## 💡 Tips untuk Kadet
- Jangan hapus file `package-lock.json`
- Jangan push `node_modules/` ke GitHub
- Baca dokumentasi package yang kamu install
- Mulai latihan lewat proyek kecil: CLI tools atau script otomatisasi

---

> "Node dan NPM membuka gerbang ke dunia ekosistem JavaScript modern. Kuasai ini, dan kamu akan lebih bebas bereksperimen." 🚀

