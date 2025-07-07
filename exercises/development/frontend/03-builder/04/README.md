# Exercise 04: Testing & Best Practice 🧪

> **Track**: Development  
> **Specialty**: Frontend  
> **Level**: 🧱 Builder  
> **Estimated Time**: 2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Menulis unit test untuk komponen React
- Memahami testing library (React Testing Library/Jest)
- Refactor struktur project agar scalable
- Menerapkan best practice frontend (naming, modularisasi, dsb.)

---

## 📖 Studi Kasus

> Kamu membangun aplikasi SPA yang mulai kompleks. Untuk menjaga kualitas, kamu perlu menulis test untuk komponen utama dan merapikan struktur project agar mudah dikembangkan tim.

---

## 🛠 Tools & Setup

- Lanjutkan dari project sebelumnya
- Install React Testing Library dan Jest

```bash
npm install --save-dev @testing-library/react jest
```

---

## 🔧 Tugas Utama

1. Buat minimal 3 unit test untuk komponen utama (Header, Main, dsb.)
2. Refactor struktur folder agar scalable (pisahkan hooks, utils, dsb.)
3. Terapkan best practice: naming, modularisasi, reusable component
4. Dokumentasikan struktur project di README

---

## ✨ Bonus Challenge

- Tambahkan test untuk custom hook
- Coverage report sederhana
- Integrasi CI (GitHub Actions)

---

## 📁 Struktur File

```
spa-starter/
├── src/
│   ├── components/
│   ├── hooks/
│   ├── utils/
│   ├── __tests__/
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
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Jest Docs](https://jestjs.io/)
- [Best Practice React](https://react.dev/learn/thinking-in-react)

---

> "Testing dan struktur rapi = aplikasi frontend yang scalable dan minim bug." 