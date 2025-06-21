# 🧪 Exercise 04: Mini UI Kit – 🌿 Explorer

> **Track**: Development\
> **Specialty**: Frontend\
> **Difficulty**: 🌿 Explorer\
> **Estimated Time**: 4–6 jam\
> **Last Updated**: Juni 2025

## 🎯 Learning Objectives

-

---

## 🧩 Studi Kasus Nyata: Design System Sederhana

Kamu bergabung dengan tim desain dan frontend di proyek startup. Tim ingin membuat UI Kit internal (kumpulan komponen siap pakai) untuk digunakan di berbagai halaman, agar konsisten dan cepat dikembangkan.

Tugas kamu: membuat beberapa komponen mandiri (tanpa framework) yang mudah digunakan ulang.

---

## 📋 Requirements

### Komponen Wajib:

1. **Card** – berisi gambar, judul, deskripsi, dan tombol
2. **Modal (Popup)** – muncul saat tombol diklik, bisa ditutup
3. **Tabs** – navigasi antar konten

### Struktur Modular:

```
exercise-04-mini-ui-kit/
├── index.html
├── components/
│   ├── card.html
│   ├── modal.html
│   └── tabs.html
├── styles/
│   ├── base.css
│   ├── card.css
│   ├── modal.css
│   └── tabs.css
├── scripts/
│   ├── modal.js
│   └── tabs.js
└── README.md
```

### Bonus (Opsional):

- Buat versi tema gelap & terang (dark/light mode)
- Tambahkan animasi transisi (fade, slide, zoom)

---

## 📥 Submission Format

```
submissions/development/frontend/[username]/mini-ui-kit/
├── index.html
├── components/
├── styles/
├── scripts/
└── README.md
```

---

## 🧠 Tips

- Komponen = gabungan HTML, CSS, dan JS → satu fungsi mandiri
- Gunakan `<template>` untuk mendefinisikan struktur card jika ingin reuse lebih dinamis
- Gunakan BEM atau kebijakan penamaan class konsisten
- Fokus pada satu komponen dulu, baru lanjut yang lain

---

## 🎯 Penilaian

| Kriteria             | Minimal          | Baik                | Unggul                        |
| -------------------- | ---------------- | ------------------- | ----------------------------- |
| Reusability Komponen | Tersusun rapi    | Mudah dipakai ulang | Modular + dokumentasi singkat |
| Interaktivitas       | Fungsi dasar     | UX halus & transisi | Terasa seperti mini-framework |
| Struktur File        | Rapi & terpisah  | Modular & skalabel  | Standar industry-ready        |
| Konsistensi UI       | Visual konsisten | Tema/warna seragam  | Tersedia 2+ varian/style      |

---

> "Membangun komponen UI bukan soal teknis, tapi tentang menciptakan bahasa visual dan interaksi yang bisa dipahami oleh semua halaman di aplikasi kita." 🧩✨

