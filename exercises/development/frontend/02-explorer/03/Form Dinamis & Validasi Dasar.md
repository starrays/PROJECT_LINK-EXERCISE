# 🧪 Exercise 03: Form Dinamis & Validasi Dasar – 🌿 Explorer

> **Track**: Development\
> **Specialty**: Frontend\
> **Difficulty**: 🌿 Explorer\
> **Estimated Time**: 3–5 jam\
> **Last Updated**: Juni 2025

## 🎯 Learning Objectives

-

---

## 🧩 Studi Kasus Nyata: Formulir Pendaftaran Kelas Online

Bayangkan kamu sedang membangun website pelatihan daring. Tim konten meminta halaman pendaftaran peserta yang terdiri dari:

- Nama lengkap
- Email
- Pilihan kelas
- Catatan tambahan (opsional)

Form ini harus responsif, mudah diisi, dan memberikan feedback jika ada kesalahan.

---

## 📋 Requirements

### Struktur Form:

- Gunakan elemen HTML form yang sesuai: `<input>`, `<select>`, `<textarea>`
- Tambahkan label yang jelas untuk setiap input
- Gunakan placeholder, required, dan atribut semantik (`type="email"`, dll)

### Validasi (Via JS):

- Cek apakah semua field wajib telah diisi
- Validasi email dengan regex dasar
- Tampilkan pesan error jika ada input yang salah
- Tampilkan pesan sukses jika form valid (tanpa submit ke server)

### Bonus (Opsional):

- Highlight field yang error
- Reset otomatis setelah sukses
- Simpan data ke `localStorage`

### Struktur Folder:

```
exercise-03-dynamic-forms-validation/
├── index.html
├── styles/style.css
├── scripts/form.js
└── README.md
```

---

## 📥 Submission Format

```
submissions/development/frontend/[username]/form-validation/
├── index.html
├── styles/style.css
├── scripts/form.js
└── README.md (opsional: preview, catatan pendek)
```

---

## 🧠 Tips

- Gunakan `form.addEventListener("submit", function(e) { ... })`
- Jangan lupa `e.preventDefault()` agar halaman tidak refresh
- Gunakan `input.classList.add("error")` untuk memberi efek visual
- Pisahkan fungsi validasi agar bisa digunakan ulang

---

## 🎯 Penilaian

| Kriteria       | Minimal            | Baik                | Unggul                       |
| -------------- | ------------------ | ------------------- | ---------------------------- |
| Struktur Form  | Lengkap & semantik | Terstruktur & rapi  | Reusable, ARIA support       |
| Validasi       | Cek dasar          | Dinamis & terhubung | Modular & bisa ditest        |
| Feedback UI/UX | Alert atau pesan   | Inline feedback     | Visual interaktif & UX ramah |
| Struktur Kode  | Tersusun           | Modular & reusable  | Mudah diperluas dan skalabel |

---

> "Form yang baik bukan hanya sekumpulan input — tapi percakapan yang nyaman antara website dan pengguna." 🧾✨

