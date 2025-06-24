# 🌐 FUNDAMENTAL – CLI & Input/Output (I/O) dengan Node.js

Latihan ini mengenalkan kamu pada cara kerja interaksi berbasis **Command Line Interface (CLI)** menggunakan Node.js. Meskipun terlihat sederhana, banyak tool profesional dan backend script dijalankan via CLI.

---

## 🧠 Apa Itu CLI?

**CLI (Command Line Interface)** adalah antarmuka berbasis teks di mana pengguna mengetik perintah untuk menjalankan program.

> 💬 CLI ≈ ngobrol langsung dengan komputer pakai teks, bukan klik tombol.

### Contoh CLI tools di dunia nyata:

- `npm` → mengelola package
- `git` → version control
- `node` → menjalankan file JavaScript

---

## 📥 Jenis Input di CLI

| Jenis Input                | Contoh                  | Modul Node.js yang Digunakan |
| -------------------------- | ----------------------- | ---------------------------- |
| **Argumen baris perintah** | `node app.js --lang=id` | `process.argv`               |
| **Input interaktif**       | Prompt: "Nama Anda?"    | `readline`                   |

---

## ✍️ `process.argv[]` – Argumen Baris Perintah

Setiap kali kamu menjalankan program seperti:

```bash
node app.js --lang=id
```

Maka `process.argv` berisi array seperti:

```js
[ '/path/to/node', '/path/to/app.js', '--lang=id' ]
```

Untuk mengambil argumen:

```js
const args = process.argv.slice(2);
```

Gunakan ini untuk membuat fitur seperti `--lang`, `--help`, dsb.

---

## 📞 `readline` – Input Interaktif

Untuk berinteraksi langsung dengan pengguna saat program berjalan:

```js
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question('Nama kamu siapa? ', (jawaban) => {
  console.log(`Halo, ${jawaban}!`);
  rl.close();
});
```

### Urutan Pertanyaan dengan `async/await`

```js
const ask = (q) => new Promise((res) => rl.question(q, res));
```

---

## 💾 Menyimpan ke File

Node.js menyediakan module `fs`:

```js
const fs = require('fs');
fs.writeFileSync('output.txt', 'Isi yang ingin disimpan');
```

> Gunakan untuk menyimpan hasil input pengguna seperti resume survey.

---

## 🧩 Format Output & UX CLI

| Teknik           | Tujuan                         |
| ---------------- | ------------------------------ |
| Template literal | Teks rapi & interaktif         |
| Emoji            | Bikin CLI lebih human friendly |
| Validasi input   | Cegah error atau input kosong  |

Contoh output CLI yang rapi:

```bash
📋 Resume:
Nama  : Raka
Umur  : 22
Minat : Backend
```

---

## 🔗 Referensi CLI Node.js

- [Node.js readline module](https://nodejs.org/api/readline.html)
- [Command Line Arguments – Node.js Docs](https://nodejs.org/en/learn/getting-started/how-to-parse-command-line-arguments/)
- [Zellwk CLI tutorial](https://zellwk.com/blog/cli/)

---

## 💬 Refleksi

- Apa perbedaan antara CLI tool dan aplikasi web?
- Apa keunggulan CLI untuk tool backend?
- Apa manfaat memisahkan logic I/O dan logic pemrosesan?

---

> "Kalau API itu jembatan antara aplikasi, maka CLI adalah pintu masuk langsung ke kekuatan sistem. Ringan, cepat, dan efisien." 🔧🖥️

