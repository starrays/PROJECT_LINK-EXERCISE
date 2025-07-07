# 🧱 FUNDAMENTAL – Testing & Best Practice di Frontend

Testing dan struktur project yang baik adalah kunci aplikasi frontend yang scalable dan minim bug.

---

## 🧪 Unit Testing Komponen

- **Unit test**: Menguji satuan kecil kode (komponen, fungsi)
- React Testing Library: Tool utama untuk test komponen React
- Contoh test:

```jsx
import { render, screen } from '@testing-library/react';
import Header from '../components/Header';

test('menampilkan judul', () => {
  render(<Header title="Dashboard" />);
  expect(screen.getByText(/Dashboard/i)).toBeInTheDocument();
});
```

---

## 🗂️ Struktur Project Scalable

- Pisahkan folder: `components/`, `hooks/`, `utils/`, `__tests__/`
- Gunakan naming yang konsisten
- Modularisasi komponen dan logic

---

## 💡 Best Practice

- Komponen kecil, reusable, dan pure
- Gunakan prop-types atau TypeScript untuk validasi props
- Dokumentasikan struktur dan logic utama di README
- Integrasi CI untuk test otomatis

---

## 🔗 Referensi
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Jest Docs](https://jestjs.io/)
- [Best Practice React](https://react.dev/learn/thinking-in-react)

---

> "Testing = jaminan kualitas. Struktur rapi = tim happy." 