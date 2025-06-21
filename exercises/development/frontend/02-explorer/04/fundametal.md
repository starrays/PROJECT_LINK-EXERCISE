# 📚 FUNDAMENTAL: Mini UI Kit – Penjelasan Mendalam

Pada latihan ini, kamu akan mempelajari bagaimana membangun **komponen UI (User Interface)** yang modular dan reusable. Pendekatan ini sangat penting dalam pengembangan web modern karena membantu developer bekerja lebih cepat, lebih rapi, dan lebih konsisten.

---

## 🧱 Apa Itu Komponen UI?

**Komponen UI** adalah bagian kecil dari antarmuka pengguna yang memiliki fungsionalitas dan tampilan mandiri, dan dapat digunakan ulang di banyak tempat. Komponen biasanya terdiri dari:

- Struktur (HTML)
- Gaya (CSS)
- Interaksi (JavaScript)

### Contoh Komponen:

- **Card**: Gambar + Judul + Deskripsi + Tombol
- **Modal**: Popup yang muncul saat tombol diklik
- **Tabs**: Navigasi antar bagian konten

---

## 🎛️ Mengapa Harus Modular?

> Bayangkan UI seperti membangun rumah dengan LEGO — kamu tidak perlu membuat ulang dinding, jendela, atau pintu dari nol setiap kali.

Modularitas membantu kamu:

- Mengurangi duplikasi kode
- Memudahkan kolaborasi tim
- Mempercepat pengembangan
- Menyederhanakan perawatan jangka panjang

---

## 📦 Struktur Folder Rekomendasi

```txt
components/   → kumpulan komponen HTML
styles/       → CSS terpisah per komponen
scripts/      → logika JS per komponen
```

Kamu bisa menggabungkan semua ini melalui `index.html` utama agar hasilnya bisa diuji secara keseluruhan.

---

## 🧠 Istilah Penting

| Istilah      | Penjelasan Mudah                                            |
| ------------ | ----------------------------------------------------------- |
| **Komponen** | Unit UI mandiri dan reusable                                |
| **Modular**  | Tersusun dari bagian kecil yang bisa digabung atau diubah   |
| **Template** | Struktur dasar HTML yang bisa di-"kloning" atau diisi ulang |
| **Event**    | Tindakan pengguna seperti klik atau hover                   |
| **BEM**      | Metode penamaan class agar struktur CSS rapi dan konsisten  |

---

## ✨ Tips Implementasi

### 🔹 Card

- Buat wrapper `.card`
- Gunakan gambar, heading (`<h3>`), paragraf, dan tombol
- Tambahkan hover effect untuk kesan profesional

### 🔹 Modal

- Sembunyikan modal dengan `display: none` / `.hidden`
- Gunakan `classList.add()` dan `.remove()` untuk buka/tutup
- Tambahkan overlay background agar fokus tetap pada modal

### 🔹 Tabs

- Gunakan class `.tab-button` dan `.tab-content`
- Aktifkan 1 tab dan sembunyikan sisanya
- Gunakan JS untuk mengatur tab aktif saat tombol ditekan

### 🔹 Bonus: Theme Toggle

- Gunakan class `dark` pada `body`
- Tambahkan CSS khusus untuk `.dark` mode
- Toggle dengan tombol dan `classList.toggle("dark")`

---

## 🚀 Menuju Framework

Latihan ini adalah mini versi dari cara kerja framework modern seperti:

- **React**: Component berbasis function dan props
- **Vue**: Template + style + script per file
- **Svelte**: Component single-file dengan reactivity bawaan

Dengan memahami struktur UI Kit ini, kamu siap melangkah ke level **Builder**.

---

## 📚 Referensi Tambahan

- [BEM 101 – CSS Tricks](https://css-tricks.com/bem-101/)
- [MDN – Web Components Overview](https://developer.mozilla.org/en-US/docs/Web/Web_Components)
- [Tailwind UI](https://tailwindui.com/components)
- [Headless UI – Aksesibilitas Komponen](https://headlessui.dev/)

---

## ✅ Checklist Mini UI Kit

-

---

> "Framework bisa diganti, tapi cara berpikir komponen adalah fondasi. Pelajari sekarang, kuasai apa pun setelahnya." 🧠🧩

