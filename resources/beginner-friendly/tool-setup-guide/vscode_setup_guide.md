# 🛠 VS Code: Panduan Setup untuk Pemula

**Visual Studio Code (VS Code)** adalah editor kode sumber yang ringan, cepat, dan sangat populer di kalangan developer, terutama pemula. Cocok untuk web development, data science, hingga DevOps.

---

## 🔧 1. Instalasi VS Code

### 🖥️ Download:
- Website resmi: [https://code.visualstudio.com](https://code.visualstudio.com)
- Tersedia untuk Windows, macOS, dan Linux

### 📦 Alternatif via package manager:
- Windows: `winget install Microsoft.VisualStudioCode`
- macOS: `brew install --cask visual-studio-code`
- Ubuntu/Linux: `sudo snap install code --classic`

---

## 🎨 2. Konfigurasi Awal

### Tema dan Font:
- Masuk ke `Preferences > Color Theme`
- Coba: `One Dark Pro`, `Night Owl`, `Dracula`
- Font yang populer: `Fira Code`, `JetBrains Mono` (aktifkan ligature di settings)

### Bahasa Indonesia:
- Install extension: `Indonesian Language Pack for VS Code`

### Format Otomatis:
- `settings.json`:
```json
"editor.formatOnSave": true,
"editor.tabSize": 2
```

---

## 🧩 3. Rekomendasi Extension

| Kategori    | Extension                | Fungsi                                 |
|-------------|---------------------------|-----------------------------------------|
| Web         | Live Server               | Preview HTML langsung di browser        |
| Frontend    | Prettier                  | Format kode otomatis                    |
| Git         | GitLens                   | Visualisasi histori dan blame Git       |
| Lainnya     | Auto Rename Tag           | Rename otomatis tag HTML/XML berpasangan|

---

## 🧪 4. VS Code & GitHub

- VS Code bisa langsung terhubung ke GitHub
- Gunakan: `Source Control > Clone Repository`
- Setelah login GitHub, kamu bisa push/pull tanpa CLI

---

## 📖 Tips Penggunaan Cepat

| Shortcut            | Aksi                                       |
|---------------------|---------------------------------------------|
| `Ctrl+P`            | Cari file cepat                            |
| `Ctrl+Shift+P`      | Command Palette (akses semua fitur)        |
| `Alt+Shift+F`       | Format file aktif                          |
| `Ctrl+Backtick`     | Buka Terminal di dalam VS Code             |

---

## 🔁 Alternatif Selain VS Code

| Editor       | Kelebihan                           |
|--------------|--------------------------------------|
| **Sublime Text** | Ringan, cepat, bisa tanpa install     |
| **Atom**         | UI menarik, cocok untuk pemula       |
| **VSCodium**     | VS Code versi open source murni      |
| **Web-based**    | [Replit](https://replit.com), [StackBlitz](https://stackblitz.com) untuk latihan cepat tanpa install

---

## 📚 Referensi Tambahan
- [Official Docs](https://code.visualstudio.com/docs)
- [VS Code Shortcuts Cheat Sheet (PDF)](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [GitHub + VS Code Integration](https://code.visualstudio.com/docs/editor/github)

---

> "Editor bukan hanya tempat menulis kode — tapi alat berpikir. VS Code membantu kamu fokus dan berkembang." 💡

