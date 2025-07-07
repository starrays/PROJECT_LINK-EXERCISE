# Exercise 02: API Documentation & Testing 📄

> **Track**: Development  
> **Specialty**: Backend  
> **Level**: 🌳 Builder  
> **Estimated Time**: 1.5–2 jam  
> **Last Updated**: Juli 2025

---

## 🎯 Tujuan Pembelajaran

- Mendokumentasikan endpoint API dengan Swagger/OpenAPI
- Membuat dan menjalankan test API dengan Postman
- Menulis kontrak API (request/response)
- Memahami pentingnya dokumentasi dan testing dalam pengembangan backend

---

## 📖 Studi Kasus

> Kamu sudah membangun API CRUD. Sekarang, tim frontend dan QA membutuhkan dokumentasi endpoint yang jelas dan test otomatis untuk memastikan API selalu berjalan sesuai kontrak.

---

## 🛠 Tools & Setup

```bash
npm install swagger-ui-express yamljs
# atau gunakan swagger-editor online
```

- Gunakan Postman/Thunder Client untuk testing
- Buat file `swagger.yaml` atau `swagger.json`

---

## 🔧 Tugas Utama

1. Buat dokumentasi API dengan Swagger (OpenAPI)
2. Integrasikan Swagger UI ke Express (`/docs` endpoint)
3. Buat minimal 5 test case di Postman (GET, POST, PUT, DELETE, error)
4. Simpan file collection test di repo
5. Tulis kontrak API: request, response, status code

---

## ✨ Bonus Challenge

- Automasi test dengan `jest`/`supertest`
- Coverage report sederhana
- Dokumentasi error response

---

## 📁 Struktur File

```
exercise-02-api-docs-testing/
├── app.js
├── swagger.yaml
├── postman_collection.json
├── README.md
├── fundamental.md
└── docs/
```

---

## ✅ Submission

```
submissions/backend/[username]/exercise-02-api-docs-testing/
├── app.js
├── swagger.yaml
├── postman_collection.json
├── README.md
└── REFLECTION.md
```

---

## 🔗 Referensi
- [Swagger/OpenAPI](https://swagger.io/docs/)
- [Postman Docs](https://learning.postman.com/)
- [Supertest](https://github.com/visionmedia/supertest)
- [Jest](https://jestjs.io/)

---

> "Dokumentasi dan testing adalah jaminan kualitas dan kolaborasi dalam tim backend." 