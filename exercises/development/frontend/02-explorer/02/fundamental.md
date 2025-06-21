# 📚 FUNDAMENTAL: DOM Interaktif & Komponen Mini – Penjelasan Mendalam

Di latihan ini, kamu akan belajar membuat elemen halaman web menjadi **hidup** melalui interaksi pengguna. Inilah langkah lanjutan dari JavaScript dasar: kamu tidak hanya menulis "kode jalan", tapi membangun **komponen UI** kecil yang bisa digunakan ulang.

---

## 🧠 Apa Itu DOM?

**DOM (Document Object Model)** adalah representasi struktur HTML dalam bentuk pohon (tree) yang bisa diakses dan dimanipulasi menggunakan JavaScript.

### 🧱 Analogi Sederhana:

Bayangkan HTML adalah "denah rumah". DOM adalah versi digital dari rumah itu yang bisa kamu ubah dari remote:

- Pindahkan sofa → ubah posisi elemen
- Nyalakan lampu → tambahkan class
- Ganti warna cat → ubah style via JS

---

## 🎮 Interaksi DOM (DOM Interaction)

Dengan JavaScript, kamu bisa:

- Menemukan elemen (`getElementById`, `querySelector`)
- Menambahkan/menghapus class (`classList.add/remove/toggle`)
- Merespon event seperti klik, hover, ketik (`addEventListener`)
- Mengubah isi teks atau atribut (`textContent`, `setAttribute`)

```js
document.getElementById("toggleBtn").addEventListener("click", function() {
  document.getElementById("jawaban").classList.toggle("hidden");
});
```

---

## 🔁 Komponen UI: Apa dan Kenapa?

**Komponen UI** adalah bagian kecil dari tampilan yang memiliki fungsi mandiri. Contohnya:

- Accordion
- Tab Navigasi
- Dropdown menu
- Modal (popup)

### Kenapa Penting?

- Bisa digunakan berulang kali (reusable)
- Mudah dirawat dan dikembangkan
- Struktur kode lebih rapi dan modular

### Perumpamaan:

> Komponen UI itu seperti LEGO: kamu bisa pakai satu blok untuk banyak bentuk yang berbeda, daripada selalu membangun dari nol.

---

## ✨ Konsep Kunci

| Konsep             | Penjelasan Mudah                                               |
| ------------------ | -------------------------------------------------------------- |
| `addEventListener` | Fungsi untuk mendeteksi dan merespon aksi pengguna             |
| `querySelector`    | Cara memilih elemen HTML dari JS, seperti CSS selector         |
| `classList.toggle` | Menambah/menghapus class secara bergantian                     |
| `dataset`          | Menyimpan data khusus di elemen HTML tanpa mengganggu struktur |
| Reusability        | Membuat 1 komponen yang bisa dipakai untuk 10 elemen berbeda   |

---

## 🧭 Struktur File Modular

Direkomendasikan untuk memisahkan kode:

```
index.html          # Struktur & konten
styles/style.css    # Styling visual
scripts/main.js     # Logika interaktif
```

> Hal ini mempermudah debugging, kolaborasi tim, dan pemeliharaan jangka panjang.

---

## 📌 Best Practice DOM Interaktif

- Jangan gunakan `onclick` langsung di HTML (gunakan event listener JS)
- Gunakan class seperti `.hidden`, `.active` untuk mengatur tampilan
- Jangan duplikasi fungsi — buat satu fungsi reusable yang bisa dipakai banyak elemen

---

## 🔗 Referensi Tambahan

- [MDN – Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [MDN – addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [JavaScript.info – DOM Manipulation](https://javascript.info/dom-nodes)

### Interaktif:

- [JavaScript30 – Vanilla JS Practice](https://javascript30.com/)

---

## ✅ Tips untuk Kadet

- Gunakan `console.log()` untuk melihat isi elemen / debug
- Cek bahwa script JS kamu dimuat **setelah** elemen HTML muncul
- Belajar berpikir "component-based", bukan hanya "page-based"
- Latihan dengan membuat ulang fitur yang kamu lihat di website sehari-hari

---

> "DOM bukan hanya pohon dari elemen HTML. Ia adalah arena di mana logika, pengalaman pengguna, dan kreativitas bertemu." 🌳✨

