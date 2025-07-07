# 🌳 FUNDAMENTAL – API Documentation & Testing

Dokumentasi dan testing adalah dua pilar penting dalam pengembangan backend profesional. Tanpa keduanya, kolaborasi dan kualitas API akan sulit dijaga.

---

## 📄 Apa Itu API Documentation?

- **API documentation** adalah deskripsi formal endpoint, request, response, dan error yang bisa diakses oleh developer lain (frontend, QA, dsb).
- Standar industri: **OpenAPI/Swagger**.
- Swagger UI memungkinkan dokumentasi interaktif dan auto-generated.

---

## 🛠️ Swagger/OpenAPI

- **Swagger** adalah tool untuk mendeskripsikan API secara terstruktur (YAML/JSON).
- Bisa diintegrasikan ke Express via `swagger-ui-express`.
- Contoh endpoint dokumentasi:

```yaml
paths:
  /notes:
    get:
      summary: Get all notes
      responses:
        '200':
          description: Success
```

---

## 🧪 API Testing

- **Testing** memastikan API berjalan sesuai kontrak.
- Manual: Postman, Thunder Client
- Otomatis: `jest`, `supertest`
- Test case minimal: sukses, error, edge case

---

## 💡 Best Practice

- Dokumentasi selalu update setiap ada perubahan endpoint
- Simpan file collection test di repo
- Automasi test untuk regression
- Dokumentasi error response dan status code

---

## 🔗 Referensi
- [Swagger/OpenAPI](https://swagger.io/docs/)
- [Postman Docs](https://learning.postman.com/)
- [Supertest](https://github.com/visionmedia/supertest)
- [Jest](https://jestjs.io/)

---

> "API yang baik = API yang terdokumentasi dan teruji." 