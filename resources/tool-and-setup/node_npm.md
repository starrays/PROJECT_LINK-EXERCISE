# 📦 Node.js & NPM – Panduan Lengkap untuk Semua Kalangan

**Node.js** adalah runtime JavaScript di luar browser, dan **NPM** adalah package manager untuk mengelola library JS. Keduanya penting untuk development modern, baik frontend maupun backend.

---

## 1️⃣ Instalasi Node.js & NPM
- Download: [https://nodejs.org](https://nodejs.org)
- Pilih versi **LTS** (Long-Term Support) untuk stabilitas
- Ikuti petunjuk instalasi sesuai OS
- Cek versi: `node -v` dan `npm -v`

---

## 2️⃣ Inisialisasi & Penggunaan Dasar

### a. Inisialisasi Proyek
```bash
npm init -y
```
Akan membuat file `package.json` otomatis.

### b. Install Package
```bash
npm install [nama-library]
```
Contoh: `npm install express`

### c. Menjalankan Script
Tambahkan di `package.json`:
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

## 3️⃣ Struktur Proyek Node Dasar
```
my-app/
├── index.js
├── package.json
├── node_modules/ (otomatis)
└── .gitignore (abaikan node_modules di Git)
```

---

## 4️⃣ Troubleshooting Umum
- **Gagal install package?** Cek koneksi internet, coba `npm cache clean --force`
- **node_modules terlalu besar?** Jangan di-push ke GitHub, gunakan `.gitignore`
- **Error versi Node/NPM?** Update ke versi terbaru dari website resmi

---

## 5️⃣ FAQ

**Q: Apa bedanya Node.js dan NPM?**
A: Node.js = runtime, NPM = package manager.

**Q: Apakah wajib pakai NPM?**
A: Untuk proyek JS modern, ya. Bisa juga pakai Yarn/PNPM, tapi NPM sudah cukup untuk pemula.

**Q: Bagaimana install package global?**
A: `npm install -g [nama]` (misal: `npm install -g nodemon`)

**Q: Bagaimana update package?**
A: `npm update [nama]` atau semua: `npm update`

---

> "Node & NPM membuka gerbang ke ekosistem JavaScript modern. Kuasai ini, kamu akan lebih bebas bereksperimen!" 