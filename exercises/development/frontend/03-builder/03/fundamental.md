# 🧱 FUNDAMENTAL – State Management & Context di React

State adalah data yang menentukan tampilan dan perilaku aplikasi. Di aplikasi besar, pengelolaan state yang baik sangat penting.

---

## 🗂️ State Lokal vs Global

- **State lokal**: Data yang hanya dipakai di satu komponen (useState)
- **State global**: Data yang dibutuhkan banyak komponen (user, theme, dsb.)

---

## 🔼 Lifting State & Prop Drilling

- **Lifting state**: Memindahkan state ke parent agar bisa diakses child lain
- **Prop drilling**: Mengoper state lewat banyak level props (bisa jadi masalah di app besar)

---

## 🌐 Context API

- Solusi prop drilling: Context API
- Buat context dengan `createContext`, sediakan value di provider, konsumsi di komponen manapun

```jsx
import { createContext, useContext } from 'react';

const UserContext = createContext();

function App() {
  return (
    <UserContext.Provider value={user}>
      <Header />
    </UserContext.Provider>
  );
}

function Header() {
  const user = useContext(UserContext);
  return <div>Hi, {user.name}</div>;
}
```

---

## 💡 Tips

- Gunakan custom hook untuk context agar lebih clean
- Untuk state kompleks, pertimbangkan Redux/Zustand
- Persist state penting ke localStorage

---

## 🔗 Referensi
- [React Context](https://react.dev/reference/react/createContext)
- [State Management Patterns](https://react.dev/learn/scaling-up-with-reducer-and-context)
- [Redux](https://redux.js.org/)

---

> "State dan context = pondasi aplikasi frontend yang scalable." 