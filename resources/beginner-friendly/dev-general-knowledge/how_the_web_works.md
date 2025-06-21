# 🌐 How the Web Works – Pengetahuan Dasar Developer

Jika kamu ingin menjadi web developer, hal pertama yang wajib kamu pahami adalah: **bagaimana web bekerja di balik layar**. Ini adalah fondasi dari semua yang akan kamu pelajari ke depannya.

---

## 🔁 Alur Sederhana Web

1. **Kamu buka browser dan ketik alamat website (URL)**
2. **Browser mengirim permintaan ke server lewat internet (HTTP request)**
3. **Server mengirim balasan (HTML, CSS, JS, data API)**
4. **Browser menampilkan halaman web berdasarkan file yang diterima**

> Setiap kali kamu klik, ketik, atau reload – browser dan server sedang "berbicara".

---

## 🧱 Komponen Utama Web

| Komponen     | Fungsi                                                       |
|--------------|--------------------------------------------------------------|
| Browser      | Menampilkan halaman web (Chrome, Firefox, Edge, Safari)     |
| Server       | Tempat menyimpan & mengirim file web ke pengguna            |
| Domain       | Alamat yang mudah diingat (example.com)                     |
| IP Address   | Alamat komputer/server di internet (angka)                  |
| DNS          | Penerjemah domain ke IP address                             |
| HTTP/S       | Protokol komunikasi antara browser ↔ server                 |

---

## 🔍 Contoh Situasi Nyata

- Kamu buka `tokopedia.com`
- Browser akan cari IP dari nama domain itu lewat **DNS**
- Setelah dapat IP, browser kirim permintaan HTTP ke server Tokopedia
- Server balas dengan file HTML, CSS, JS → ditampilkan di browsermu

---

## 🛠 Tools Terkait
- **DevTools (Network tab)** → untuk lihat permintaan & file yang dikirim
- **Postman** → untuk testing request/response (API)
- **nslookup / ping** → untuk cek DNS/IP via terminal

---

## 🔐 HTTPS vs HTTP
- **HTTP** = data dikirim terbuka (kurang aman)
- **HTTPS** = data dienkripsi (standar modern, aman untuk transaksi)

> Kalau kamu buka website yang belum HTTPS, browser akan beri peringatan ⚠️

---

## 📚 Referensi Tambahan
- [MDN - How the Web Works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works)
- [FrontendMasters - Internet Fundamentals](https://frontendmasters.com/courses/internet/)
- [Visual: What Happens When...](https://github.com/alex/what-happens-when)

---

> "Memahami cara kerja web seperti belajar anatomi tubuh manusia — kamu jadi tahu cara memperbaiki, mengoptimalkan, dan membangun sesuatu dengan benar." 🧬🌍

