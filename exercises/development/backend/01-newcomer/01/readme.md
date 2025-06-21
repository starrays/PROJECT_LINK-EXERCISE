# 📦 Exercise 01 – Introduction to API

Selamat datang di latihan pertama backend level **Newcomer**. Di sini kamu akan membuat server sederhana dan menghasilkan **JSON response** yang bisa diakses lewat browser atau tools seperti Postman.

---

## 🎯 Tujuan

- Memahami apa itu API (Application Programming Interface)
- Belajar membuat server lokal menggunakan Node.js
- Mengirimkan response dalam format JSON

---

## 🧪 Studi Kasus

> Kamu diminta membuat endpoint sederhana untuk aplikasi *Student Directory*. Saat endpoint `/students` diakses, maka sistem akan mengembalikan daftar siswa dalam format JSON.

Contoh:

```json
[
  { "id": 1, "name": "Alya", "major": "Informatika" },
  { "id": 2, "name": "Rama", "major": "Sistem Informasi" }
]
```

---

## 🔧 Instruksi

1. Buat folder `ex01-intro-api`
2. Buat file `server.js`
3. Gunakan modul `http` bawaan Node.js
4. Buat endpoint `GET /students` yang mengembalikan data JSON
5. Jalankan server dengan perintah `node server.js`
6. Tes di browser (`localhost:3000/students`) atau Postman

---

## 📂 Struktur Minimal

```
ex01-intro-api/
├── server.js
└── students.json (optional, jika ingin memisahkan data)
```

---

## 📌 Checklist

-

---

## 🚀 Tantangan Lanjutan

- Tambahkan endpoint baru: `/info` yang menampilkan data project kamu
- Simpan data di file eksternal (`students.json`) lalu load menggunakan `fs.readFile`

---

> "Sebuah API sederhana bisa jadi pintu awal menuju sistem besar dan kompleks. Kuasai yang kecil dulu, baru bangun lebih besar." 🧠

