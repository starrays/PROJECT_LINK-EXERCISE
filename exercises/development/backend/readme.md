# 🧠 Backend Development Track – PROJECT_LINK

Selamat datang di jalur pembelajaran **Backend Development** komunitas PROJECT_LINK!  
Track ini dirancang bagi pemula hingga calon profesional yang ingin memahami logika di balik sistem backend — dari membuat API sederhana, mengelola data, hingga membangun sistem backend modular, aman, dan efisien.

---

## 🚀 Tujuan Track Backend

Dengan mengikuti track ini, peserta akan:
- Mengerti dasar komunikasi HTTP, API, dan server
- Mampu membangun REST API dari nol menggunakan Node.js
- Memahami struktur backend modern (routing, middleware, modularisasi)
- Mengintegrasikan penyimpanan data menggunakan file system dan database
- Mengenal praktik pengamanan dan skalabilitas backend

---

## 📚 Struktur Level & Exercise

Track ini terdiri dari 4 level: 🌱 Newcomer → 🌿 Explorer → 🌳 Builder → 🚀 Innovator

### 🌱 Newcomer – "Mengenal Dunia Backend"
> Fokus: HTTP, struktur file, input/output, REST dasar (tanpa framework)

| No. | Judul Exercise               | Fokus Pembelajaran                             |
|-----|------------------------------|-------------------------------------------------|
| 01  | Intro to API & HTTP          | HTTP Method, status code, JSON, REST dasar     |
| 02  | CLI & Input-Output           | Node CLI, arg parsing, terminal logic          |
| 03  | Routing & Filesystem Basics  | Manual routing, `fs.readFile`, simpan file     |
| 04  | Modular Server Structure     | Code split, folder layout sederhana            |

📦 Tools: `Node.js`, `http`, Postman/Thunder Client, Terminal

---

### 🌿 Explorer – "Express API & Error Handling"
> Fokus: Express.js, middleware, input validation, simple auth

| No. | Judul Exercise               | Fokus Pembelajaran                              |
|-----|------------------------------|--------------------------------------------------|
| 01  | Building API with Express    | Route, method, request body                     |
| 02  | Middleware & Error Handling  | Custom MW, `next()`, error logging              |
| 03  | Dynamic Data File Storage    | Data persistent via JSON & `fs.writeFile`       |
| 04  | Simple Auth Simulation       | Protected route, simple token & role logic      |

📦 Tools: `Express.js`, Postman, Node.js

---

### 🌳 Builder – "API + Database Integration"
> Fokus: CRUD API, SQLite, testing, API documentation

| No. | Judul Exercise                 | Fokus Pembelajaran                            |
|-----|--------------------------------|------------------------------------------------|
| 01  | REST API + SQLite Integration  | CRUD DB, SQL dasar, table schema              |
| 02  | API Documentation & Testing    | Swagger, Postman test, request contract       |
| 03  | Relational Data & Joins        | Relationship (1:N, M:N), query optimization   |
| 04  | MVC Structure API              | Controller, router, model separation          |

📦 Tools: `SQLite`, `Knex.js`, `Swagger`, `Postman`, `Express`

---

### 🚀 Innovator – "Scalable & Secure Backend"
> Fokus: performance, microservice mindset, security, API versioning

| No. | Judul Exercise                   | Fokus Pembelajaran                               |
|-----|----------------------------------|---------------------------------------------------|
| 01  | Performance & Refactor Audit     | Lighthouse API audit, Artillery benchmark         |
| 02  | API Versioning & Rate Limiting   | Versioning pattern, abuse protection middleware   |
| 03  | Service Separation Simulation    | Microservice mindset, modular REST endpoint       |
| 04  | Secure API with JWT & Helmet     | Auth, CORS, header-based protection               |

📦 Tools: `JWT`, `Helmet`, `Express-rate-limit`, `Artillery`, `Postman`

---

## 🛠️ Tools & Teknologi yang Digunakan

| Kategori      | Tool/Platform                  |
|---------------|-------------------------------|
| Runtime       | Node.js                        |
| Framework     | Express.js                     |
| REST Client   | Postman, Thunder Client, curl  |
| DB            | SQLite (Builder), JSON file    |
| Testing       | Swagger, Postman Test, Artillery|
| DevTools      | VS Code, Prettier, ESLint      |
| Version Control | Git, GitHub                   |

---

## 📁 Struktur Folder
```
backend/
├── README.md                    ← Panduan umum track backend
├── newcomer/
│   ├── README.md                ← Ringkasan level pemula
│   ├── exercise-01-intro-api/
│   │   ├── README.md
│   │   └── fundamental.md
│   ├── exercise-02-cli-io/
│   └── ...
├── explorer/
│   ├── README.md
│   ├── exercise-01-express-api/
│   └── ...
├── builder/
│   ├── README.md
│   ├── exercise-01-db-integration/
│   └── ...
└── innovator/
    ├── README.md
    ├── exercise-01-api-audit/
    └── ...
```

---

## 📤 Submission Format
```
submissions/backend/[username]/[exercise-name]/
├── README.md                     ← Penjelasan tugas dan konfigurasi
├── src/
│   └── server.js / app.js        ← File kode utama
├── docs/
│   └── API-contract.md / screenshot ← Dokumentasi / bukti hasil
└── REFLECTION.md                 ← Catatan pembelajaran & evaluasi pribadi
```
---

## 📚 Referensi Luar

- [MDN Web Docs – HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- [Node.js Documentation](https://nodejs.org/en/docs)
- [Express.js Guide](https://expressjs.com/)
- [Postman Docs](https://learning.postman.com/)
- [RESTful API Design Patterns](https://restfulapi.net/)

---

## 🤝 Kontribusi

Track ini bersifat terbuka dan kolaboratif. Kamu bisa:
- Mengajukan PR untuk latihan baru
- Menyumbang fundamental.md atau contoh starter
- Memberikan review terhadap submission kadet lain

---

## 🔄 Roadmap Perluasan (Coming Soon)
- Pengantar REST + GraphQL (lanjutan)
- Deployment via Railway / Render
- Microservice dengan Message Queue (MQ Simulasi)
- Cloud Functions / Serverless API

---

Siap untuk jadi Backend Warrior? 🌐💪  
Mulailah dari level yang sesuai dengan skill-mu, dan jadikan folder ini sebagai ruang latihan kamu untuk membangun backend berkualitas industri!

