# 🧪 Exercise 01: Responsive Layout & Media Query – 🌿 Explorer

> **Track**: Development  
> **Specialty**: Frontend  
> **Difficulty**: 🌿 Explorer  
> **Estimated Time**: 2–4 jam  
> **Last Updated**: Juni 2025

## 🎯 Learning Objectives

- [ ] Membangun layout web responsive menggunakan Flexbox dan Grid
- [ ] Menggunakan media query untuk menyesuaikan tampilan berdasarkan ukuran layar
- [ ] Menerapkan struktur folder dan file CSS modular sederhana
- [ ] Mengenali perbedaan antara desktop-first dan mobile-first approach

---

## 🧩 Studi Kasus Nyata: Halaman Produk Online

Bayangkan kamu adalah frontend developer di startup e-commerce lokal. Tim desainer UI mengirimkan wireframe untuk halaman detail produk, dan kamu diminta mengubahnya menjadi halaman web yang:

- Dapat dibuka di smartphone, tablet, dan desktop
- Layout gambar dan deskripsi bisa beradaptasi saat ukuran layar berubah
- Tombol beli tetap terlihat jelas di semua ukuran layar

Ini adalah **situasi nyata** yang sering dihadapi frontend developer setiap hari.

---

## 📋 Requirements

### Struktur Konten:
- Header dengan nama toko dan navigasi sederhana
- Section utama berisi:
  - Gambar produk (ukuran besar)
  - Deskripsi produk (judul, harga, dan deskripsi singkat)
  - Tombol "Beli Sekarang"
- Footer berisi kontak sosial

### Fungsionalitas:
- Menggunakan Flexbox/Grid untuk menyusun gambar dan teks
- Menggunakan media query agar layout berubah di berbagai ukuran layar:
  - >1024px (desktop): gambar dan teks berdampingan
  - 768px–1023px (tablet): gambar di atas, teks di bawah
  - <768px (mobile): stack vertikal + tombol sticky di bawah

### Struktur Folder
```
exercise-01-responsive-layout/
├── index.html
├── styles/
│   └── style.css
└── README.md
```

---

## 🛠 Tools
- VS Code + Live Server / CodeSandbox
- DevTools di browser (Chrome/Edge)

---

## 🧠 Tips
- Gunakan class seperti `.container`, `.product-card`, `.product-image`, `.product-info`
- Mulailah dengan mobile-first layout, lalu tambahkan media query untuk tablet & desktop
- Tes di ukuran layar berbeda (DevTools: Responsive Mode)

---

## 📥 Submission Format
```
submissions/development/frontend/[username]/responsive-layout/
├── index.html
├── styles/style.css
└── README.md (opsional: deskripsi dan preview screenshot)
```

---

## 🎯 Penilaian

| Kriteria               | Minimal | Baik         | Unggul                      |
|------------------------|---------|--------------|-----------------------------|
| Struktur HTML & CSS    | Valid   | Bersih       | Semantik dan modular        |
| Responsivitas Layout   | OK      | Smooth       | Elegan di semua ukuran layar|
| Penggunaan Flex/Grid   | Sederhana| Efisien      | Kombinasi efektif           |
| Media Query            | 1-2     | 3 breakpoints| Konsisten dan adaptif       |
| UI & UX                | Fungsi  | Nyaman       | Estetis dan profesional     |

---

> "Responsiveness bukan fitur tambahan, tapi *standar* bagi web modern. Ini bukan tentang mengecilkan halaman, tapi membuat pengalaman tetap optimal di setiap perangkat." 📱💻

