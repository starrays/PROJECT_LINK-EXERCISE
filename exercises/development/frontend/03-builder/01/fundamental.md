# 🧱 FUNDAMENTAL – SPA, Struktur Project & Komponen Dasar

Pada level Builder, kamu akan membangun aplikasi Single Page Application (SPA) dengan React. SPA memungkinkan pengalaman pengguna yang mulus tanpa reload halaman penuh.

---

## ⚛️ Apa Itu SPA?

- **SPA (Single Page Application)**: Aplikasi web yang hanya memuat satu halaman HTML, navigasi dan update konten dilakukan secara dinamis via JavaScript.
- Contoh: Gmail, Trello, Notion.

---

## 🗂️ Struktur Folder Project

- **src/components/**: Komponen UI reusable (Header, Footer, dsb.)
- **src/pages/**: Halaman utama aplikasi (Home, About, dsb.)
- **src/assets/**: Gambar, ikon, file statis
- **src/App.js**: Root komponen aplikasi
- **src/index.js**: Entry point aplikasi

---

## 🧩 Komponen Dasar React

- Komponen = fungsi yang mengembalikan JSX
- Props = data yang dikirim ke komponen
- Contoh:

```jsx
function Header({ title }) {
  return <header><h1>{title}</h1></header>;
}
```

- Komponen bisa diimpor dan digunakan di App.js

---

## 💡 Tips

- Gunakan props untuk membuat komponen dinamis
- Pisahkan komponen sesuai tanggung jawab
- Struktur folder rapi = scaling mudah

---

## 🔗 Referensi
- [React Components](https://react.dev/learn/your-first-component)
- [SPA Concept](https://developer.mozilla.org/en-US/docs/Glossary/SPA)
- [Vite + React](https://vitejs.dev/guide/)

---

> "SPA dan komponen adalah pondasi utama frontend modern. Kuasai dasarnya, kamu siap membangun aplikasi apapun!" 