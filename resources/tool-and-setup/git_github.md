# 🧠 Git & GitHub – Panduan Lengkap untuk Semua Kalangan

**Git** adalah alat version control (pengontrol versi) dan **GitHub** adalah platform kolaborasi kode berbasis web. Keduanya wajib dikuasai oleh siapa pun yang ingin belajar coding modern, baik sendiri maupun tim.

---

## 1️⃣ Apa Itu Git & GitHub?
- **Git:** Sistem untuk melacak perubahan file/kode, bisa kembali ke versi sebelumnya, dan memudahkan kolaborasi.
- **GitHub:** Tempat menyimpan repo Git secara online, kolaborasi, review, dan dokumentasi proyek.

---

## 2️⃣ Instalasi & Setup Awal

### a. Install Git
- Download: [https://git-scm.com](https://git-scm.com)
- Ikuti petunjuk instalasi sesuai OS (Windows, Mac, Linux)
- Cek versi: `git --version`

### b. Konfigurasi Identitas
```bash
git config --global user.name "namamu"
git config --global user.email "email@domain.com"
```

### c. Buat Akun GitHub
- Daftar di [https://github.com](https://github.com)
- Lengkapi profil (bio, foto, repo public pertama)

---

## 3️⃣ Alur Kerja Dasar Git + GitHub

| Langkah      | Perintah / Aksi                     |
| ------------ | ----------------------------------- |
| Clone Repo   | `git clone [url]`                   |
| Cek status   | `git status`                        |
| Tambah file  | `git add .` atau `git add namafile` |
| Commit       | `git commit -m "pesan commit"`      |
| Push         | `git push origin main`              |
| Tarik update | `git pull`                          |

### Contoh Alur Kerja:
1. Buat repo di GitHub
2. Clone ke lokal: `git clone https://github.com/username/nama-repo.git`
3. Tambah/edit file, lalu:
   - `git add .`
   - `git commit -m "deskripsi perubahan"`
   - `git push origin main`
4. Lihat perubahan di GitHub

---

## 4️⃣ Kolaborasi & Pull Request
- Fork repo jika ingin kontribusi ke proyek orang lain
- Buat branch baru untuk fitur/bugfix: `git checkout -b nama-branch`
- Setelah selesai, push branch dan buat Pull Request di GitHub
- Diskusikan perubahan, minta review, dan merge jika sudah oke

---

## 5️⃣ Troubleshooting Umum
- **Gagal push?** Cek koneksi internet, pastikan sudah login GitHub
- **Conflict saat merge?** Baca pesan error, edit file yang konflik, lalu commit ulang
- **Lupa commit?** Jalankan `git status` untuk cek perubahan yang belum disimpan
- **Repo terlalu besar?** Jangan commit file besar (video, node_modules, dsb)

---

## 6️⃣ FAQ

**Q: Apa bedanya Git dan GitHub?**
A: Git = alat lokal, GitHub = platform online untuk repo Git.

**Q: Apakah GitHub gratis?**
A: Ya, untuk repo public dan private (dengan batasan tertentu).

**Q: Apakah harus selalu pakai terminal?**
A: Tidak. Ada aplikasi GUI seperti GitHub Desktop, Sourcetree, dsb.

**Q: Bagaimana jika lupa perintah Git?**
A: Cek [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) atau gunakan `git help`.

---

> "Git & GitHub adalah fondasi kerja tim modern. Kuasai dasarnya, kamu akan jauh lebih percaya diri berkolaborasi!" 