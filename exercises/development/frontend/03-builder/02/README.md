# Exercise 02: Konsumsi API & Data Fetching 🌐

> **Track**: Development  
> **Specialty**: Frontend  
> **Level**: 🧱 Builder  
> **Estimated Time**: 2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Mengambil data dari REST API menggunakan fetch/axios
- Menampilkan data dinamis di komponen
- Menangani loading, error, dan empty state
- Memahami lifecycle dan useEffect di React

---

## 📖 Studi Kasus

> Kamu akan membangun halaman dashboard yang menampilkan data dari API publik (misal: JSONPlaceholder, PokeAPI, dsb). Data harus di-fetch saat komponen mount dan ditampilkan secara dinamis.

---

## 🛠 Tools & Setup

- Lanjutkan dari project exercise 01
- Gunakan fetch API atau axios

---

## 🔧 Tugas Utama

1. Buat halaman baru (misal: `UsersPage` atau `PostsPage`)
2. Fetch data dari API publik di useEffect
3. Tampilkan data dalam bentuk list/table/card
4. Tampilkan loading indicator saat fetch
5. Tampilkan error message jika fetch gagal
6. Tampilkan pesan jika data kosong

---

## ✨ Bonus Challenge

- Tambahkan fitur search/filter
- Pagination sederhana
- Gunakan custom hook untuk data fetching

---

## 📁 Struktur File

```
spa-starter/
├── src/
│   ├── components/
│   ├── pages/
│   │   └── UsersPage.jsx
│   ├── App.js
│   └── ...
├── README.md
└── fundamental.md
```

---

## ✅ Submission

```
submissions/frontend/[username]/spa-starter/
├── src/
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi
- [React useEffect](https://react.dev/reference/react/useEffect)
- [MDN Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [Axios Docs](https://axios-http.com/)

---

> "Mengambil dan menampilkan data dari API adalah skill inti frontend modern." 