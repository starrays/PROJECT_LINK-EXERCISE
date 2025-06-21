# 📚 FUNDAMENTAL: Dasar Interaksi JavaScript di Halaman Web

Setelah menguasai HTML (struktur) dan CSS (tampilan), saatnya mengenal **JavaScript (JS)** — bahasa pemrograman yang membuat halaman web menjadi hidup dan interaktif.

---

## ⚡ Apa Itu JavaScript?
JavaScript adalah bahasa pemrograman utama di dunia web. Ia memungkinkan kamu untuk:
- Menangani aksi pengguna (klik, input, hover)
- Mengubah isi halaman secara dinamis
- Membuat animasi, form interaktif, validasi, popup, dan banyak lagi

### Analogi Sederhana:
> Jika HTML adalah kerangka dan CSS adalah tampilan, maka JavaScript adalah "otak" dan "otot" dari halamanmu — ia mengatur logika dan interaksi.

---

## 🧠 Struktur Dasar JavaScript
JavaScript bisa ditulis di dalam `<script>` di HTML, atau di file terpisah (`script.js`). Disarankan menggunakan file terpisah agar lebih rapi.

```html
<script src="script.js"></script>
```

### Contoh: Ubah warna background
```js
document.body.style.backgroundColor = "lightblue";
```

---

## 🎮 Interaksi Dasar: Event & DOM

### DOM = Document Object Model

JavaScript dapat mengakses dan memanipulasi elemen HTML melalui struktur bernama **DOM**.

```js
document.getElementById("judul")
```

### Event = Tindakan pengguna

Contoh event: klik tombol, isi input, scroll halaman, dsb.

```js
const btn = document.getElementById("tombol");
btn.onclick = function() {
  alert("Tombol diklik!");
};
```

---

## 🧩 Elemen Dasar JavaScript untuk Pemula

| Konsep      | Contoh Kode                           |
|-------------|----------------------------------------|
| Variabel    | `let nama = "Kadet";`                 |
| Fungsi      | `function salam() { ... }`             |
| Kondisi     | `if (nilai > 80) { ... }`              |
| Event       | `element.onclick = function() { ... }` |
| DOM Select  | `getElementById`, `querySelector`      |

---

## 🎯 Tujuan Latihan Ini
- Menghubungkan file JS ke HTML
- Membuat tombol yang memberi respons (event listener)
- Mengubah isi dan tampilan halaman secara interaktif

---

## 💡 Bonus untuk Dipahami
- Gunakan `console.log()` untuk mengecek variabel & debugging
- Hindari duplikasi `id`, gunakan `class` untuk elemen ganda
- Pelajari `addEventListener()` untuk cara modern menangani event

```js
btn.addEventListener("click", function() {
  console.log("Diklik!");
});
```

---

## 🔗 Referensi Tambahan
- [MDN – JavaScript First Steps](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps)
- [W3Schools – JavaScript](https://www.w3schools.com/js/)
- [JavaScript.info – Modern JS](https://javascript.info/)
- [FreeCodeCamp – JS Course](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/)

### Video:
- [Codevolution – JavaScript for Beginners](https://www.youtube.com/watch?v=PkZNo7MFNFg)

---

## ✅ Tips untuk Kadet
- Sering-sering cek hasil kerja di browser
- Biasakan buka console (Ctrl+Shift+I → tab Console)
- Mulai dari interaksi sederhana, lalu eksplorasi lebih jauh

---

> "JavaScript membuat web bukan hanya tampil, tapi bisa bicara balik padamu." 🧠💻

