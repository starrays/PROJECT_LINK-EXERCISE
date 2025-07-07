# Exercise 03: State Management & Context 🗂️

> **Track**: Development  
> **Specialty**: Frontend  
> **Level**: 🧱 Builder  
> **Estimated Time**: 2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Mengelola state global dan lokal di React
- Memahami lifting state, prop drilling, dan context
- Membuat context provider untuk state global
- Refactor komponen agar lebih scalable

---

## 📖 Studi Kasus

> Kamu membangun aplikasi dashboard dengan fitur user login dan theme (dark/light). State user dan theme harus bisa diakses dari banyak komponen tanpa prop drilling berlebihan.

---

## 🛠 Tools & Setup

- Lanjutkan dari project sebelumnya
- Gunakan React Context API
- Optional: Redux/Zustand

---

## 🔧 Tugas Utama

1. Buat context untuk user dan theme
2. Implementasi context provider di App.js
3. Gunakan context di beberapa komponen (Header, Main, dsb.)
4. Demonstrasikan lifting state dan prop drilling
5. Refactor agar state global mudah diakses

---

## ✨ Bonus Challenge

- Persist state ke localStorage
- Tambahkan toggle theme (dark/light)
- Gunakan custom hook untuk context

---

## 📁 Struktur File

```
spa-starter/
├── src/
│   ├── context/
│   │   └── UserContext.js
│   │   └── ThemeContext.js
│   ├── components/
│   ├── pages/
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
- [React Context](https://react.dev/reference/react/createContext)
- [State Management Patterns](https://react.dev/learn/scaling-up-with-reducer-and-context)
- [Redux](https://redux.js.org/)

---

> "State global dan context = kunci aplikasi frontend yang scalable dan maintainable." 