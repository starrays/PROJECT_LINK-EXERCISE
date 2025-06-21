# 🧠 Git & GitHub: Panduan Dasar untuk Pemula

Git dan GitHub adalah dua alat yang wajib dipahami oleh siapa pun yang belajar coding secara kolaboratif. Tanpa keduanya, kerja tim modern nyaris mustahil.

---

## 🔧 Apa Itu Git?

- **Git** adalah sistem version control (pengontrol versi) yang memungkinkan kamu menyimpan, melacak, dan memulihkan versi kode yang kamu kerjakan.
- Mirip seperti "riwayat perubahan" di Google Docs, tapi jauh lebih canggih.

### 🔁 Perumpamaan:

> Git seperti mesin waktu: kamu bisa kembali ke kondisi file kapan pun kamu mau.

---

## 🌐 Apa Itu GitHub?

- **GitHub** adalah platform berbasis web untuk menyimpan proyek Git secara online.
- Menyediakan kolaborasi, pull request, issue tracker, dan integrasi dengan tool modern lainnya.

> Tanpa GitHub, Git hanya bekerja di lokal. Dengan GitHub, proyekmu bisa dikerjakan bareng-bareng secara online.

---

## ⚙️ Cara Setup Git dan GitHub

### 1. Install Git:

- Download: [https://git-scm.com](https://git-scm.com)
- Cek versi: `git --version`

### 2. Konfigurasi Git Awal:

```bash
git config --global user.name "namamu"
git config --global user.email "email@domain.com"
```

### 3. Buat Akun GitHub:

- Kunjungi: [https://github.com](https://github.com)
- Lengkapi profil (bio, foto, repo public pertama)

---

## 📥 Alur Kerja Git + GitHub (Dasar)

| Langkah      | Perintah / Aksi                     |
| ------------ | ----------------------------------- |
| Clone Repo   | `git clone [url]`                   |
| Cek status   | `git status`                        |
| Tambah file  | `git add .` atau `git add namafile` |
| Commit       | `git commit -m "pesan commit"`      |
| Push         | `git push origin main`              |
| Tarik update | `git pull`                          |

---

## 🧪 Praktik Wajib Kadet

1. Buat repo GitHub dengan nama `project-link-exercise`
2. Clone ke lokal dengan `git clone`
3. Tambahkan folder dan isi hasil latihan
4. Commit + push hasil ke GitHub
5. Buat Pull Request jika ada integrasi dengan tim

---

## 🧠 Tips Umum

- Commit harus deskriptif, bukan "update 1"
- Push secara berkala, jangan tunggu menumpuk
- Satu folder → satu repo → satu tanggung jawab
- Gunakan `.gitignore` untuk folder yang tidak perlu di-push (seperti `node_modules/`)

---

## 🔁 Alternatif GitHub

| Platform      | Keterangan                     |
| ------------- | ------------------------------ |
| **GitLab**    | Open source, mirip GitHub      |
| **Bitbucket** | Terintegrasi dengan Atlassian  |
| **Gitea**     | Lightweight self-hosted GitHub |

---

## 🔗 Referensi Tambahan

- [Git Book (Bahasa Indonesia)](https://git-scm.com/book/id/v2)
- [GitHub Docs for Beginners](https://docs.github.com/en/get-started/)
- [Visual Git Cheat Sheet](https://ndpsoftware.com/git-cheatsheet.html)

---

> "Dengan Git dan GitHub, kamu tidak hanya menyimpan kode, tapi membangun sejarah kerja yang bisa kamu banggakan." 🧩

