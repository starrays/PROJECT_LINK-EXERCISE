# Exercise 02: CLI & Input/Output (I/O) 🖥️

> **Track**: Development\
> **Specialty**: Backend\
> **Level**: 🌱 Newcomer\
> **Estimated Time**: 1–2 jam\
> **Last Updated**: Juni 2025

---

## 🎯 Tujuan Pembelajaran

- Mengenal cara kerja program berbasis CLI (Command Line Interface)
- Belajar menangkap input dari pengguna via terminal
- Memproses argumen (`process.argv`) dan input interaktif (`readline`)
- Menampilkan output yang informatif, terstruktur, dan dinamis

---

## 📖 Studi Kasus

> Kamu ditugaskan membuat tool CLI sederhana bernama `form-wizard.js` yang menjalankan survey interaktif di terminal. Tool ini akan menanyakan nama, umur, dan minat pengguna, lalu menampilkan hasilnya secara rapi.

---

## 🛠 Tools & Setup

| Alat     | Deskripsi                        |
| -------- | -------------------------------- |
| Node.js  | Menjalankan program CLI          |
| Terminal | Jalankan perintah dan input data |
| VS Code  | Editor dengan integrasi terminal |

### Struktur Awal

```bash
mkdir exercise-02-cli-io
cd exercise-02-cli-io
npm init -y
touch form-wizard.js
```

---

## 🔧 Tugas Utama

Buat file `form-wizard.js` yang:

1. Menyapa pengguna: "Selamat datang di Form Wizard!"
2. Bertanya:
   - Nama lengkap
   - Usia
   - Minat utama dalam IT (Frontend, Backend, Data, UI/UX, lainnya)
3. Setelah input, tampilkan output seperti:

```
📋 Resume Pendaftaran:
Nama   : Raka Pratama
Umur   : 21
Minat  : Backend
Terima kasih sudah mengisi form!
```

4. Gunakan `readline` module bawaan Node.js
5. Pastikan CLI tetap berjalan hingga semua pertanyaan selesai

---

## ✨ Bonus Challenge

- Tambahkan validasi usia agar harus berupa angka
- Simpan hasil input ke file `result.txt`
- Tambahkan argumen opsional seperti:

```bash
node form-wizard.js --lang=en
```

Agar pesan tampil dalam Bahasa Inggris

---

## 📁 Struktur File Disarankan

```
exercise-02-cli-io/
├── form-wizard.js
├── README.md
├── fundamental.md
└── result.txt (optional)
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-02-cli-io/
├── form-wizard.js
├── README.md
└── REFLECTION.md
```

---

## 💡 Tips & Resources

- Gunakan `readline.question()` secara berurutan dengan callback atau `async/await`
- Format output menggunakan template string agar rapi
- Cek validasi angka dengan `Number.isNaN()` atau regex

---

Happy Hacking via Terminal ⚡

