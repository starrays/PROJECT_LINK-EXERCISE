# 🧪 Exercise 03: JavaScript Basic Interaction

## 🎯 Tujuan

Memahami interaksi dasar menggunakan JavaScript seperti menangani event, mengubah elemen DOM, dan membuat logika sederhana di halaman web.

## 📚 Prasyarat

- Sudah menyelesaikan HTML dan CSS dasar

## 🛠 Tools

- Browser
- CodePen / JSFiddle / Replit
- (Opsional) VS Code + Live Server

## 📦 File yang Harus Dibuat

- `index.html`
- `style.css`
- `script.js`

## 📋 Instruksi

1. **Gunakan kembali struktur HTML + CSS sebelumnya.**

2. **Tambahkan tombol di bawah deskripsi:**

```html
<button id="changeColorBtn">Ubah Warna Background</button>
```

3. **Buat file **``** dan hubungkan:**

```html
<script src="script.js"></script>
```

4. **Logika interaksi:**

   - Saat tombol ditekan, ubah warna background `body` menjadi acak
   - Tampilkan alert jika warna telah berubah

5. **Tambahkan input nama dan tombol submit:**

   - Ketika user isi nama dan klik tombol, tampilkan "Halo, [nama]!" di bawahnya menggunakan JavaScript

## 💡 Contoh Kode

```js
document.getElementById("changeColorBtn").onclick = function() {
  const colors = ["#f4f4f4", "#e0f7fa", "#ffebee", "#f3e5f5"];
  const chosen = colors[Math.floor(Math.random() * colors.length)];
  document.body.style.backgroundColor = chosen;
  alert("Background diubah!");
};
```

## 🧠 Bonus Challenge

- Tambahkan jam digital yang real-time (`setInterval` + `Date()`)
- Buat toggle antara light/dark mode

## ✅ Checklist

-

## 📌 Contoh Preview



## 📥 Penyerahan

Folder: `submissions/frontend/newcomer/[namamu]-js-interaction/`

## 🙋 Tips

- Konsisten pakai `id` untuk akses elemen
- Debug pakai `console.log` jika error
- Gunakan event listener (`onclick`, `addEventListener`) secara fleksibel

---

> "JavaScript memberi nyawa pada halaman webmu. Belajar sedikit, lalu eksplor tanpa batas." ⚡

