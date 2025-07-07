# 🧱 FUNDAMENTAL – Data Fetching & State di React

Mengambil data dari API dan menampilkannya secara dinamis adalah skill inti frontend modern.

---

## 🌐 Data Fetching di React

- **fetch()**: API bawaan browser untuk HTTP request
- **axios**: Library populer untuk HTTP request
- Data fetching biasanya dilakukan di lifecycle mount (useEffect)

---

## ⚛️ useEffect untuk Fetch Data

- useEffect dipakai untuk menjalankan side effect (seperti fetch data) setelah komponen render

```jsx
import { useEffect, useState } from 'react';

useEffect(() => {
  fetch('https://jsonplaceholder.typicode.com/users')
    .then(res => res.json())
    .then(data => setUsers(data));
}, []);
```

---

## ⏳ Loading & Error State

- Selalu sediakan state untuk loading dan error
- Contoh:

```jsx
const [loading, setLoading] = useState(true);
const [error, setError] = useState(null);

if (loading) return <p>Loading...</p>;
if (error) return <p>Error: {error.message}</p>;
```

---

## 💡 Tips

- Gunakan custom hook untuk reusable data fetching
- Selalu handle empty state (data kosong)
- Pisahkan komponen list/item untuk modularitas

---

## 🔗 Referensi
- [React useEffect](https://react.dev/reference/react/useEffect)
- [MDN Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [Axios Docs](https://axios-http.com/)

---

> "Frontend modern = data dinamis. Kuasai data fetching, kamu siap integrasi dengan backend manapun!" 