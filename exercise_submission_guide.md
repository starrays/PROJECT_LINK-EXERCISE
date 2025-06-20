# 📘 Panduan Lengkap: Submit Exercise PROJECT_LINK untuk Kadet

Panduan ini membantu kamu (kadet) langkah demi langkah, mulai dari membuat akun GitHub hingga submit hasil latihan melalui pull request (PR) ke repositori komunitas `project-link-exercises`.

---

## 🧩 1. Buat & Siapkan Akun GitHub

### Langkah:
1. Kunjungi: [https://github.com](https://github.com)
2. Klik `Sign up` dan ikuti proses registrasi
3. Verifikasi email & login ke akun kamu

### Setelah Login:
- Atur nama pengguna yang profesional (ex: `namadepan-namabelakang`)
- Tambahkan foto profil dan bio singkat (optional tapi disarankan)

---

## 🔧 2. Fork Repositori Project-Link Exercises

### Langkah:
1. Buka repositori utama komunitas: [https://github.com/LEX-DEV141/PROJECT_LINK-EXERCISE.git](https://github.com/LEX-DEV141/PROJECT_LINK-EXERCISE.git)
2. Klik tombol `Fork` di kanan atas → pilih akun GitHub kamu

> Ini akan membuat salinan repositori di akun kamu, tempat kamu bisa bekerja bebas.

---

## 📁 3. Clone Repo ke Komputer (Opsional)
> Kalau kamu ingin mengedit langsung di lokal (offline):

```bash
# Buka terminal lalu jalankan:
git clone https://github.com/username-kamu/project-link-exercises.git
cd project-link-exercises
```

> Ganti `username-kamu` dengan nama pengguna GitHub kamu.

---

## 🔍 4. Baca dan Pilih Exercise

### Lokasi Exercise:
```
exercises/
└── development/
    └── frontend/
        └── newcomer/
            └── exercise-01-html-intro/
```

### Langkah:
1. Buka file `README.md` dalam folder latihan
2. Baca instruksi, prasyarat, dan format pengerjaan
3. Kerjakan sesuai petunjuk menggunakan CodePen, VS Code, atau tools lain

---

## 🧪 5. Kerjakan Exercise dan Simpan

### Format Folder Hasil:
```
submissions/development/frontend/username-kamu/nama-exercise/
├── index.html
├── style.css / script.js (jika ada)
├── README.md (opsional: deskripsi atau preview)
└── REFLECTION.md (opsional: catatan belajarmu)
```

> Buat direktori ini di dalam repositori hasil fork-mu. Gunakan struktur yang rapi dan konsisten.

---

## 🔄 6. Commit dan Push ke GitHub

```bash
# Tambahkan perubahan ke Git
git add .

# Buat commit
git commit -m "submit exercise-01-html-intro by username-kamu"

# Push ke GitHub
git push origin main  # atau nama branch kamu
```

---

## 📬 7. Buat Pull Request (PR)

### Langkah:
1. Buka repositori fork kamu di GitHub
2. Akan muncul tombol `Contribute` → klik `Open pull request`
3. Tambahkan deskripsi PR, misalnya:
```
[Submission] exercise-01-html-intro by username-kamu
- Selesai struktur dasar HTML
- Tambah bonus: list hobi
```
4. Kirim Pull Request ke branch `main` di repositori utama `project-link-exercises`

---

## 🧑‍🤝‍🧑 8. Request Review

1. Setelah PR dibuat, mention reviewer/mentor:
```
@mentor-username tolong review 🙏
```
2. Perbaiki jika ada feedback, lalu push ulang:
```bash
git add .
git commit -m "fix: perbaikan hasil review mentor"
git push
```

---

## ✅ 9. Selesai dan Tercatat!

Jika PR kamu sudah di-approve dan di-merge oleh tim mentor:
- Exercise kamu dinyatakan selesai
- Progress kamu bisa dimasukkan ke leaderboard atau dashboard komunitas

---

## 🔁 Tips & Best Practices

- Gunakan nama folder & file yang konsisten
- Tambahkan `README.md` berisi preview hasil (opsional tapi disarankan)
- Rajin update fork kamu jika repositori utama berubah:
```bash
git remote add upstream https://github.com/project-link/project-link-exercises.git
git pull upstream main
```

---

## 💬 Butuh Bantuan?
- Gabung Discord komunitas dan tanya di kanal `#exercise-help`
- Lihat panduan tambahan di folder `resources/`
- Minta pairing dengan mentor lewat kanal `#mentorship`

---

> "Jangan tunggu ahli untuk mulai. Mulai, dan dalam proses, kamu jadi ahli." 🚀

