# 📚 FUNDAMENTAL: Dasar-Dasar CSS & Layout Web

Setelah mempelajari HTML sebagai struktur dasar web, sekarang saatnya mengenal **CSS** – bahasa yang bertugas mendandani tampilan halaman web kamu agar menarik, nyaman dibaca, dan responsive.

---

## 🎨 Apa Itu CSS?

**CSS (Cascading Style Sheets)** adalah bahasa yang digunakan untuk mendesain dan mengatur tampilan (style) elemen HTML di halaman web. CSS mengontrol warna, ukuran font, posisi elemen, jarak antar elemen, dan bahkan animasi!

### Analogi Sederhana:

- Kalau HTML adalah *tulang dan organ tubuh*, maka CSS adalah *pakaian dan gaya rambut*. Fungsinya tetap sama, tapi tampilannya bisa sangat berbeda.

---

## 💡 Mengapa Harus Pakai CSS Terpisah?

Kita bisa menulis CSS langsung di HTML, tapi penulisan **CSS dalam file terpisah** (`style.css`) membuat:

- Kode lebih rapi dan terorganisir
- Lebih mudah dipelihara dan digunakan ulang
- Cepat dipahami oleh tim/mentor lain

```html
<link rel="stylesheet" href="style.css" />
```

---

## 🧱 Konsep Dasar CSS

### 1. **Selector** – memilih elemen

```css
h1 {
  color: blue;
}
```

> Ini berarti: semua elemen `<h1>` akan berwarna biru.

### 2. **Properti dan Nilai** – aturan styling

```css
p {
  font-size: 16px;
  text-align: justify;
}
```

### 3. **Box Model** – fondasi tata letak web

Setiap elemen HTML dianggap seperti "kotak":

```
[margin]
 [border]
  [padding]
   [content]
```

### 4. **Class dan ID**

```html
<p class="intro">Halo dunia!</p>
```

```css
.intro {
  color: green;
}
```

### 5. **Flexbox (dasar)**

Untuk layout horizontal/vertikal yang fleksibel

```css
.container {
  display: flex;
  justify-content: center;
  gap: 20px;
}
```

---

## 📐 Layout dan Responsif

### Mengatur Lebar Konten

```css
.container {
  max-width: 600px;
  margin: auto;
}
```

### Mobile-Friendly

Gunakan unit `em`, `rem`, `%`, dan hindari ukuran fix seperti `px` di layout utama agar bisa menyesuaikan layar.

---

## 🎯 Tujuan Latihan Ini

- Membuat halaman HTML yang lebih enak dilihat
- Menerapkan prinsip CSS dasar seperti warna, font, dan spacing
- Menggunakan Flexbox sederhana untuk menata elemen secara horizontal

---

## 🔗 Referensi Tambahan

- [MDN – CSS Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics)
- [CSS Tricks – Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [W3Schools – CSS Tutorial](https://www.w3schools.com/css/)
- [FreeCodeCamp – Responsive Web Design](https://www.freecodecamp.org/learn/responsive-web-design/)

### Video:

- [Traversy Media – CSS Crash Course](https://www.youtube.com/watch?v=yfoY53QXEnI)

---

## ✅ Tips untuk Kadet

- Gunakan DevTools di browser untuk eksplor dan modifikasi style secara langsung
- Mulai dengan gaya minimalis dulu, baru eksplorasi
- Konsisten dalam penggunaan indentasi dan nama class

---

> "CSS bukan tentang menjadi cantik — tapi membuat web bisa dibaca, nyaman, dan bermakna." 💅

