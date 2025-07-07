# Exercise 04: MVC Structure API 🏗️

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌳 Builder  
> **Estimated Time**: 2–3 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Memisahkan logic API ke dalam struktur MVC (Model-View-Controller)
- Membuat project backend yang modular dan maintainable
- Mengimplementasikan controller, model, router, dan utils
- Refactor API CRUD agar scalable

---

## 📖 Studi Kasus

> Kamu sudah membangun API CRUD dengan relasi database. Kini, saatnya merapikan kode ke struktur MVC agar mudah dikembangkan oleh tim dan siap untuk skala lebih besar.

---

## 🛠 Tools & Setup

- Gunakan Express.js, SQLite/Knex.js
- Struktur folder: `models/`, `controllers/`, `routes/`, `db/`, `utils/`

---

## 🔧 Tugas Utama

1. Refactor API CRUD ke struktur MVC:
   - `models/` → Query database
   - `controllers/` → Logic bisnis & validasi
   - `routes/` → Routing endpoint
   - `utils/` → Helper (error, response, dsb.)
2. Implementasi endpoint CRUD dan relasi (user, notes)
3. Tambahkan error handler modular
4. Dokumentasikan struktur project di README

---

## ✨ Bonus Challenge

- Middleware custom (logger, validator)
- Modularisasi error handler
- Unit test untuk controller/model

---

## 📁 Struktur File

```
exercise-04-mvc-structure/
├── app.js
├── models/
├── controllers/
├── routes/
├── db/
├── utils/
├── README.md
└── fundamental.md
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-04-mvc-structure/
├── app.js
├── models/
├── controllers/
├── routes/
├── db/
├── utils/
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi
- [MVC Pattern](https://developer.mozilla.org/en-US/docs/Glossary/MVC)
- [Express.js Project Structure](https://zellwk.com/blog/structure-node-js/)
- [Knex.js Docs](https://knexjs.org/)

---

> "Struktur rapi = tim happy. MVC adalah fondasi aplikasi backend modern." 