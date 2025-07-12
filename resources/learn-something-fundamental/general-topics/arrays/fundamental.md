# 📋 Arrays Fundamental

## 1. Apa itu Array?

**Array** adalah struktur data yang menyimpan kumpulan nilai dalam satu variabel. Bayangkan array seperti rak buku - setiap slot memiliki nomor urut (index) dan dapat berisi buku (nilai) yang berbeda.

### 🎯 Konsep Dasar
- **Index**: Posisi elemen dalam array (dimulai dari 0)
- **Length**: Jumlah elemen dalam array
- **Element**: Nilai yang disimpan dalam array
- **Mutable**: Array dapat diubah setelah dibuat
- **Ordered**: Elemen memiliki urutan yang tetap

### 📝 Contoh Sederhana
```javascript
// Array sederhana
let fruits = ["Apel", "Jeruk", "Mangga"];
let numbers = [1, 2, 3, 4, 5];
let mixed = ["Text", 123, true, null];

// Mengakses elemen array
console.log(fruits[0]);     // "Apel" (index 0)
console.log(fruits[1]);     // "Jeruk" (index 1)
console.log(fruits.length); // 3 (jumlah elemen)
```

### 🔍 Istilah Penting
- **Index**: Posisi elemen (0-based)
- **Element**: Nilai dalam array
- **Length**: Jumlah elemen
- **Iteration**: Proses mengakses setiap elemen
- **Mutation**: Mengubah array asli
- **Immutable**: Membuat array baru tanpa mengubah yang lama

## 2. Membuat dan Mengakses Array

### 🔧 Array Literal Syntax
```javascript
// ✅ Array literal (cara paling umum)
let fruits = ["Apel", "Jeruk", "Mangga"];
let numbers = [1, 2, 3, 4, 5];
let empty = [];

// ✅ Array dengan berbagai tipe data
let mixed = ["String", 42, true, null, undefined, { name: "Budi" }];

// ✅ Array dalam array (nested array)
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
```

### 🏗️ Array Constructor
```javascript
// ✅ Array constructor
let arr1 = new Array();           // []
let arr2 = new Array(3);          // [undefined, undefined, undefined]
let arr3 = new Array(1, 2, 3);    // [1, 2, 3]

// ✅ Array.from() untuk membuat array dari iterable
let arrayFromString = Array.from("Hello");  // ["H", "e", "l", "l", "o"]
let arrayFromSet = Array.from(new Set([1, 2, 2, 3]));  // [1, 2, 3]
```

### 📍 Indexing (Zero-based)
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ Positive indexing
console.log(fruits[0]);  // "Apel"
console.log(fruits[1]);  // "Jeruk"
console.log(fruits[2]);  // "Mangga"

// ✅ Negative indexing (dari belakang)
console.log(fruits[-1]);  // undefined (JavaScript tidak support negative index)
console.log(fruits[fruits.length - 1]);  // "Pisang" (cara manual)

// ✅ Menggunakan at() method (ES2022)
console.log(fruits.at(0));   // "Apel"
console.log(fruits.at(-1));  // "Pisang" (negative index support)
console.log(fruits.at(-2));  // "Mangga"
```

### 📏 Length Property
```javascript
let fruits = ["Apel", "Jeruk", "Mangga"];

// ✅ Mendapatkan length
console.log(fruits.length);  // 3

// ✅ Mengubah length (berhati-hati!)
fruits.length = 2;  // Menghapus elemen terakhir
console.log(fruits);  // ["Apel", "Jeruk"]

fruits.length = 5;  // Menambah elemen kosong
console.log(fruits);  // ["Apel", "Jeruk", empty × 3]

// ✅ Length selalu 1 lebih besar dari index terakhir
let arr = ["A", "B", "C"];
console.log(arr[arr.length - 1]);  // "C" (elemen terakhir)
```

## 3. Array Methods Dasar

### ➕ Adding Elements

#### push() - Menambah di akhir
```javascript
let fruits = ["Apel", "Jeruk"];

// ✅ push() - menambah elemen di akhir
fruits.push("Mangga");
console.log(fruits);  // ["Apel", "Jeruk", "Mangga"]

// ✅ push() dengan multiple elements
fruits.push("Pisang", "Anggur");
console.log(fruits);  // ["Apel", "Jeruk", "Mangga", "Pisang", "Anggur"]

// ✅ push() return length baru
let newLength = fruits.push("Stroberi");
console.log(newLength);  // 6
```

#### unshift() - Menambah di awal
```javascript
let fruits = ["Jeruk", "Mangga"];

// ✅ unshift() - menambah elemen di awal
fruits.unshift("Apel");
console.log(fruits);  // ["Apel", "Jeruk", "Mangga"]

// ✅ unshift() dengan multiple elements
fruits.unshift("Pisang", "Anggur");
console.log(fruits);  // ["Pisang", "Anggur", "Apel", "Jeruk", "Mangga"]

// ✅ unshift() return length baru
let newLength = fruits.unshift("Stroberi");
console.log(newLength);  // 6
```

### ➖ Removing Elements

#### pop() - Menghapus dari akhir
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ pop() - menghapus dan return elemen terakhir
let lastFruit = fruits.pop();
console.log(lastFruit);  // "Pisang"
console.log(fruits);     // ["Apel", "Jeruk", "Mangga"]

// ✅ pop() pada array kosong
let emptyArray = [];
let result = emptyArray.pop();
console.log(result);  // undefined
```

#### shift() - Menghapus dari awal
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ shift() - menghapus dan return elemen pertama
let firstFruit = fruits.shift();
console.log(firstFruit);  // "Apel"
console.log(fruits);      // ["Jeruk", "Mangga", "Pisang"]

// ✅ shift() pada array kosong
let emptyArray = [];
let result = emptyArray.shift();
console.log(result);  // undefined
```

### 🔄 Modifying Elements

#### splice() - Menambah/Menghapus di posisi tertentu
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ splice(start, deleteCount, ...items)
// Menghapus 2 elemen mulai dari index 1
let removed = fruits.splice(1, 2);
console.log(removed);  // ["Jeruk", "Mangga"]
console.log(fruits);   // ["Apel", "Pisang"]

// ✅ Menambah elemen di posisi tertentu
fruits.splice(1, 0, "Stroberi", "Anggur");
console.log(fruits);   // ["Apel", "Stroberi", "Anggur", "Pisang"]

// ✅ Mengganti elemen
fruits.splice(1, 1, "Jeruk");
console.log(fruits);   // ["Apel", "Jeruk", "Anggur", "Pisang"]
```

#### slice() - Mengambil bagian array (immutable)
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang", "Anggur"];

// ✅ slice(start, end) - end tidak termasuk
let firstTwo = fruits.slice(0, 2);
console.log(firstTwo);  // ["Apel", "Jeruk"]
console.log(fruits);    // ["Apel", "Jeruk", "Mangga", "Pisang", "Anggur"] (tidak berubah)

// ✅ slice() dengan negative index
let lastTwo = fruits.slice(-2);
console.log(lastTwo);   // ["Pisang", "Anggur"]

// ✅ slice() tanpa parameter - copy seluruh array
let copy = fruits.slice();
console.log(copy);      // ["Apel", "Jeruk", "Mangga", "Pisang", "Anggur"]
```

### 🔗 Combining Arrays

#### concat() - Menggabungkan array
```javascript
let fruits = ["Apel", "Jeruk"];
let vegetables = ["Tomat", "Wortel"];

// ✅ concat() - menggabungkan array
let food = fruits.concat(vegetables);
console.log(food);  // ["Apel", "Jeruk", "Tomat", "Wortel"]

// ✅ concat() dengan multiple arrays
let drinks = ["Kopi", "Teh"];
let allItems = fruits.concat(vegetables, drinks);
console.log(allItems);  // ["Apel", "Jeruk", "Tomat", "Wortel", "Kopi", "Teh"]

// ✅ concat() dengan non-array values
let mixed = fruits.concat("Pisang", 123);
console.log(mixed);  // ["Apel", "Jeruk", "Pisang", 123]
```

#### join() - Menggabungkan elemen menjadi string
```javascript
let fruits = ["Apel", "Jeruk", "Mangga"];

// ✅ join() dengan default separator
let result = fruits.join();
console.log(result);  // "Apel,Jeruk,Mangga"

// ✅ join() dengan custom separator
let result2 = fruits.join(" - ");
console.log(result2);  // "Apel - Jeruk - Mangga"

// ✅ join() dengan empty string
let result3 = fruits.join("");
console.log(result3);  // "ApelJerukMangga"

// ✅ join() dengan array yang berisi non-string
let mixed = ["Apel", 123, true];
let result4 = mixed.join(" | ");
console.log(result4);  // "Apel | 123 | true"
```

## 4. Array Iteration

### 🔄 Traditional For Loop
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ For loop dengan index
for (let i = 0; i < fruits.length; i++) {
    console.log(`Index ${i}: ${fruits[i]}`);
}

// ✅ For loop dengan break
for (let i = 0; i < fruits.length; i++) {
    if (fruits[i] === "Mangga") {
        console.log("Found Mangga!");
        break;
    }
}

// ✅ For loop dengan continue
for (let i = 0; i < fruits.length; i++) {
    if (fruits[i] === "Jeruk") {
        continue;  // Skip Jeruk
    }
    console.log(fruits[i]);
}
```

### 🔄 for...of Loop (ES6+)
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ for...of loop (mengakses nilai)
for (let fruit of fruits) {
    console.log(fruit);
}

// ✅ for...of dengan destructuring
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 }
];

for (let { name, age } of users) {
    console.log(`${name} is ${age} years old`);
}

// ✅ for...of dengan index (menggunakan entries())
for (let [index, fruit] of fruits.entries()) {
    console.log(`Index ${index}: ${fruit}`);
}
```

### 🔄 for...in Loop (Hindari untuk Array)
```javascript
let fruits = ["Apel", "Jeruk", "Mangga"];

// ⚠️ for...in loop (tidak direkomendasikan untuk array)
for (let index in fruits) {
    console.log(`Index ${index}: ${fruits[index]}`);
}

// ⚠️ Masalah dengan for...in
Array.prototype.customMethod = function() {};
for (let index in fruits) {
    console.log(index);  // Akan include "customMethod" juga
}
```

### 🔄 Array Methods untuk Iteration

#### forEach() - Iterasi sederhana
```javascript
let fruits = ["Apel", "Jeruk", "Mangga"];

// ✅ forEach() dengan callback function
fruits.forEach(function(fruit, index, array) {
    console.log(`Index ${index}: ${fruit}`);
});

// ✅ forEach() dengan arrow function
fruits.forEach((fruit, index) => {
    console.log(`${index}: ${fruit}`);
});

// ✅ forEach() dengan object
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 }
];

users.forEach(user => {
    console.log(`${user.name} is ${user.age} years old`);
});
```

#### map() - Transformasi array
```javascript
let numbers = [1, 2, 3, 4, 5];

// ✅ map() untuk transformasi
let doubled = numbers.map(num => num * 2);
console.log(doubled);  // [2, 4, 6, 8, 10]

// ✅ map() dengan object
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 }
];

let userNames = users.map(user => user.name);
console.log(userNames);  // ["Budi", "Ani"]

// ✅ map() dengan index
let fruits = ["Apel", "Jeruk", "Mangga"];
let indexedFruits = fruits.map((fruit, index) => `${index + 1}. ${fruit}`);
console.log(indexedFruits);  // ["1. Apel", "2. Jeruk", "3. Mangga"]
```

#### filter() - Menyaring array
```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// ✅ filter() untuk angka genap
let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);  // [2, 4, 6, 8, 10]

// ✅ filter() dengan object
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 },
    { name: "Charlie", age: 17 }
];

let adultUsers = users.filter(user => user.age >= 18);
console.log(adultUsers);  // [{ name: "Budi", age: 25 }, { name: "Ani", age: 30 }]

// ✅ filter() dengan multiple conditions
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];
let longFruits = fruits.filter(fruit => fruit.length > 4);
console.log(longFruits);  // ["Mangga", "Pisang"]
```

#### reduce() - Mengurangi array menjadi satu nilai
```javascript
let numbers = [1, 2, 3, 4, 5];

// ✅ reduce() untuk sum
let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum);  // 15

// ✅ reduce() untuk max
let max = numbers.reduce((max, num) => Math.max(max, num), numbers[0]);
console.log(max);  // 5

// ✅ reduce() dengan object
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 },
    { name: "Charlie", age: 22 }
];

let totalAge = users.reduce((sum, user) => sum + user.age, 0);
console.log(totalAge);  // 77

// ✅ reduce() untuk grouping
let fruits = ["Apel", "Jeruk", "Apel", "Mangga", "Jeruk"];
let fruitCount = fruits.reduce((count, fruit) => {
    count[fruit] = (count[fruit] || 0) + 1;
    return count;
}, {});
console.log(fruitCount);  // { Apel: 2, Jeruk: 2, Mangga: 1 }
```

## 5. Array Manipulation

### ➕ Adding Elements
```javascript
let fruits = ["Apel", "Jeruk"];

// ✅ Menambah di akhir
fruits.push("Mangga");

// ✅ Menambah di awal
fruits.unshift("Pisang");

// ✅ Menambah di posisi tertentu
fruits.splice(2, 0, "Stroberi");

// ✅ Menambah multiple elements
fruits.push("Anggur", "Kiwi");
```

### ➖ Removing Elements
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang", "Anggur"];

// ✅ Menghapus dari akhir
let lastFruit = fruits.pop();

// ✅ Menghapus dari awal
let firstFruit = fruits.shift();

// ✅ Menghapus dari posisi tertentu
let removed = fruits.splice(1, 2);

// ✅ Menghapus dengan filter (immutable)
let filtered = fruits.filter(fruit => fruit !== "Jeruk");
```

### 🔄 Updating Elements
```javascript
let fruits = ["Apel", "Jeruk", "Mangga"];

// ✅ Update dengan index
fruits[1] = "Pisang";

// ✅ Update dengan splice
fruits.splice(0, 1, "Stroberi");

// ✅ Update dengan map (immutable)
let updated = fruits.map(fruit => 
    fruit === "Jeruk" ? "Pisang" : fruit
);
```

### 🔍 Finding Elements
```javascript
let fruits = ["Apel", "Jeruk", "Mangga", "Pisang"];

// ✅ indexOf() - mencari index
let index = fruits.indexOf("Mangga");  // 2
let notFound = fruits.indexOf("Kiwi"); // -1

// ✅ includes() - cek keberadaan
let hasMangga = fruits.includes("Mangga");  // true
let hasKiwi = fruits.includes("Kiwi");      // false

// ✅ find() - mencari elemen pertama yang memenuhi kondisi
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 },
    { name: "Charlie", age: 22 }
];

let user = users.find(user => user.age > 25);  // { name: "Ani", age: 30 }

// ✅ findIndex() - mencari index elemen pertama yang memenuhi kondisi
let userIndex = users.findIndex(user => user.age > 25);  // 1
```

## 6. Multi-dimensional Arrays

### 📊 2D Arrays (Matrix)
```javascript
// ✅ 2D array sederhana
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// ✅ Mengakses elemen 2D array
console.log(matrix[0][1]);  // 2
console.log(matrix[1][2]);  // 6

// ✅ Iterasi 2D array
for (let i = 0; i < matrix.length; i++) {
    for (let j = 0; j < matrix[i].length; j++) {
        console.log(`matrix[${i}][${j}] = ${matrix[i][j]}`);
    }
}

// ✅ Membuat 2D array dengan fill()
let grid = Array(3).fill().map(() => Array(3).fill(0));
console.log(grid);  // [[0,0,0], [0,0,0], [0,0,0]]
```

### 🏗️ 3D Arrays
```javascript
// ✅ 3D array
let cube = [
    [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ],
    [
        [10, 11, 12],
        [13, 14, 15],
        [16, 17, 18]
    ],
    [
        [19, 20, 21],
        [22, 23, 24],
        [25, 26, 27]
    ]
];

// ✅ Mengakses elemen 3D array
console.log(cube[0][1][2]);  // 6
console.log(cube[2][2][2]);  // 27
```

### 🔗 Nested Arrays
```javascript
// ✅ Array of objects
let students = [
    { name: "Budi", grades: [85, 90, 78] },
    { name: "Ani", grades: [92, 88, 95] },
    { name: "Charlie", grades: [76, 82, 80] }
];

// ✅ Menghitung rata-rata nilai setiap siswa
students.forEach(student => {
    const average = student.grades.reduce((sum, grade) => sum + grade, 0) / student.grades.length;
    console.log(`${student.name}: ${average.toFixed(2)}`);
});

// ✅ Array dengan berbagai tipe data
let mixed = [
    "String",
    42,
    true,
    [1, 2, 3],
    { name: "Budi" },
    function() { return "Hello"; }
];
```

### 🎯 Array of Objects
```javascript
// ✅ Array of objects - data yang kompleks
let products = [
    { id: 1, name: "Laptop", price: 15000000, category: "Electronics" },
    { id: 2, name: "Mouse", price: 500000, category: "Electronics" },
    { id: 3, name: "Book", price: 150000, category: "Books" },
    { id: 4, name: "Chair", price: 2000000, category: "Furniture" }
];

// ✅ Filtering berdasarkan category
let electronics = products.filter(product => product.category === "Electronics");

// ✅ Mapping untuk mendapatkan nama produk
let productNames = products.map(product => product.name);

// ✅ Reducing untuk total harga
let totalPrice = products.reduce((sum, product) => sum + product.price, 0);

// ✅ Finding produk termahal
let mostExpensive = products.reduce((max, product) => 
    product.price > max.price ? product : max
);
```

## 7. Array Best Practices

### 🛡️ Defensive Programming
```javascript
// ✅ Validasi array sebelum operasi
function processArray(arr) {
    if (!Array.isArray(arr)) {
        throw new Error('Input must be an array');
    }
    
    if (arr.length === 0) {
        return [];
    }
    
    return arr.map(item => item * 2);
}

// ✅ Safe array access
function getElement(arr, index) {
    if (!Array.isArray(arr)) {
        return null;
    }
    
    if (index < 0 || index >= arr.length) {
        return null;
    }
    
    return arr[index];
}

// ✅ Array dengan default values
function createUserList(users = []) {
    return users.map(user => ({
        name: user.name || 'Anonymous',
        age: user.age || 0,
        email: user.email || ''
    }));
}
```

### 🔒 Immutability
```javascript
// ✅ Immutable operations
let originalFruits = ["Apel", "Jeruk", "Mangga"];

// ✅ Menambah elemen (immutable)
let newFruits = [...originalFruits, "Pisang"];

// ✅ Menghapus elemen (immutable)
let filteredFruits = originalFruits.filter(fruit => fruit !== "Jeruk");

// ✅ Update elemen (immutable)
let updatedFruits = originalFruits.map(fruit => 
    fruit === "Jeruk" ? "Pisang" : fruit
);

// ✅ Sort (immutable)
let sortedFruits = [...originalFruits].sort();

// ✅ Reverse (immutable)
let reversedFruits = [...originalFruits].reverse();
```

### 📊 Performance Optimization
```javascript
// ✅ Hindari nested loops jika memungkinkan
// ❌ Buruk
for (let i = 0; i < array1.length; i++) {
    for (let j = 0; j < array2.length; j++) {
        if (array1[i] === array2[j]) {
            // process
        }
    }
}

// ✅ Lebih baik dengan Set
let set = new Set(array2);
for (let item of array1) {
    if (set.has(item)) {
        // process
    }
}

// ✅ Gunakan for...of untuk iterasi sederhana
for (let item of array) {
    // process item
}

// ✅ Gunakan array methods untuk transformasi
let doubled = array.map(x => x * 2);
let filtered = array.filter(x => x > 0);
let sum = array.reduce((total, x) => total + x, 0);
```

## 8. Studi Kasus Praktis

### 🛒 Shopping Cart System
```javascript
// ✅ Shopping cart dengan array
class ShoppingCart {
    constructor() {
        this.items = [];
    }
    
    addItem(product) {
        const existingItem = this.items.find(item => item.id === product.id);
        
        if (existingItem) {
            existingItem.quantity += 1;
        } else {
            this.items.push({
                ...product,
                quantity: 1
            });
        }
    }
    
    removeItem(productId) {
        this.items = this.items.filter(item => item.id !== productId);
    }
    
    updateQuantity(productId, quantity) {
        const item = this.items.find(item => item.id === productId);
        if (item) {
            if (quantity <= 0) {
                this.removeItem(productId);
            } else {
                item.quantity = quantity;
            }
        }
    }
    
    getTotal() {
        return this.items.reduce((total, item) => 
            total + (item.price * item.quantity), 0
        );
    }
    
    getItemCount() {
        return this.items.reduce((count, item) => count + item.quantity, 0);
    }
    
    clear() {
        this.items = [];
    }
}

// ✅ Usage
const cart = new ShoppingCart();
cart.addItem({ id: 1, name: "Laptop", price: 15000000 });
cart.addItem({ id: 2, name: "Mouse", price: 500000 });
cart.addItem({ id: 1, name: "Laptop", price: 15000000 }); // Quantity +1

console.log(cart.getTotal());     // 15500000
console.log(cart.getItemCount()); // 3
```

### 📊 Data Analysis
```javascript
// ✅ Sales data analysis
const salesData = [
    { month: "Jan", sales: 1000, profit: 200 },
    { month: "Feb", sales: 1200, profit: 250 },
    { month: "Mar", sales: 1100, profit: 220 },
    { month: "Apr", sales: 1400, profit: 300 },
    { month: "May", sales: 1300, profit: 280 },
    { month: "Jun", sales: 1600, profit: 350 }
];

// ✅ Total sales
const totalSales = salesData.reduce((sum, data) => sum + data.sales, 0);

// ✅ Average sales
const averageSales = totalSales / salesData.length;

// ✅ Best performing month
const bestMonth = salesData.reduce((best, current) => 
    current.sales > best.sales ? current : best
);

// ✅ Sales trend (increasing/decreasing)
const salesTrend = salesData.map((data, index, array) => {
    if (index === 0) return { month: data.month, trend: "N/A" };
    const previous = array[index - 1];
    const trend = data.sales > previous.sales ? "Up" : "Down";
    return { month: data.month, trend };
});

// ✅ Monthly growth rate
const growthRates = salesData.map((data, index, array) => {
    if (index === 0) return { month: data.month, growth: 0 };
    const previous = array[index - 1];
    const growth = ((data.sales - previous.sales) / previous.sales) * 100;
    return { month: data.month, growth: growth.toFixed(2) + "%" };
});
```

### 🎮 Game State Management
```javascript
// ✅ Game board dengan 2D array
class GameBoard {
    constructor(width = 8, height = 8) {
        this.width = width;
        this.height = height;
        this.board = this.createBoard();
    }
    
    createBoard() {
        return Array(this.height).fill().map(() => 
            Array(this.width).fill(null)
        );
    }
    
    placePiece(row, col, piece) {
        if (this.isValidPosition(row, col)) {
            this.board[row][col] = piece;
            return true;
        }
        return false;
    }
    
    getPiece(row, col) {
        if (this.isValidPosition(row, col)) {
            return this.board[row][col];
        }
        return null;
    }
    
    isValidPosition(row, col) {
        return row >= 0 && row < this.height && 
               col >= 0 && col < this.width;
    }
    
    getEmptyPositions() {
        const empty = [];
        for (let row = 0; row < this.height; row++) {
            for (let col = 0; col < this.width; col++) {
                if (this.board[row][col] === null) {
                    empty.push({ row, col });
                }
            }
        }
        return empty;
    }
    
    clearBoard() {
        this.board = this.createBoard();
    }
    
    getBoardState() {
        return this.board.map(row => [...row]); // Deep copy
    }
}

// ✅ Usage
const game = new GameBoard(3, 3);
game.placePiece(0, 0, "X");
game.placePiece(1, 1, "O");
game.placePiece(2, 2, "X");

console.log(game.getBoardState());
// [
//   ["X", null, null],
//   [null, "O", null],
//   [null, null, "X"]
// ]
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- **JavaScript.info**: [Arrays](https://javascript.info/array)
- **W3Schools**: [JavaScript Arrays](https://www.w3schools.com/js/js_arrays.asp)

### 📖 Buku Rekomendasi
- "Eloquent JavaScript" by Marijn Haverbeke
- "JavaScript: The Definitive Guide" by David Flanagan
- "You Don't Know JS: Types & Grammar" by Kyle Simpson

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Arrays Tutorial
- **The Net Ninja**: JavaScript Arrays & Array Methods
- **Programming with Mosh**: JavaScript Arrays

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen array
- **JSFiddle**: Untuk testing array methods
- **Replit**: Untuk project array
- **LeetCode**: Untuk latihan algoritma dengan array

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan array sederhana
2. **Learn Methods**: Kuasai array methods satu per satu
3. **Practice Iteration**: Latihan berbagai cara iterasi
4. **Build Projects**: Aplikasikan dalam project nyata
5. **Optimize**: Pelajari best practices dan performance

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep array
2. **Practice** → Tulis kode dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki
5. **Repeat** → Ulangi dengan konsep array baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Arrays
- **freeCodeCamp**: JavaScript Array Methods
- **Scrimba**: Array tutorials
- **JavaScript30**: Array-based challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Mengakses index yang tidak ada
let fruits = ["Apel", "Jeruk"];
console.log(fruits[5]);  // undefined

// ✅ Solusi: Cek length atau gunakan at()
console.log(fruits.at(5));  // undefined (lebih aman)

// ❌ Mutasi array dalam loop
let numbers = [1, 2, 3, 4, 5];
for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] % 2 === 0) {
        numbers.splice(i, 1);  // ❌ Mengubah array saat iterasi
        i--;  // Workaround yang berbahaya
    }
}

// ✅ Solusi: Gunakan filter atau reverse loop
let filtered = numbers.filter(num => num % 2 !== 0);

// ❌ Membandingkan array dengan ===
let arr1 = [1, 2, 3];
let arr2 = [1, 2, 3];
console.log(arr1 === arr2);  // false

// ✅ Solusi: Bandingkan elemen satu per satu
function arraysEqual(arr1, arr2) {
    if (arr1.length !== arr2.length) return false;
    return arr1.every((item, index) => item === arr2[index]);
}
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.log untuk debugging array
let fruits = ["Apel", "Jeruk", "Mangga"];
console.log("Original:", fruits);
console.log("Length:", fruits.length);
console.log("First item:", fruits[0]);

// ✅ Gunakan console.table untuk array of objects
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 }
];
console.table(users);

// ✅ Gunakan JSON.stringify untuk melihat struktur
console.log(JSON.stringify(fruits, null, 2));

// ✅ Debug array methods
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(num => {
    console.log("Processing:", num);
    return num * 2;
});
console.log("Result:", doubled);
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Array Destructuring
```javascript
// ✅ Basic destructuring
let fruits = ["Apel", "Jeruk", "Mangga"];
let [first, second, third] = fruits;

// ✅ Destructuring dengan default values
let [a, b, c, d = "Default"] = ["A", "B"];

// ✅ Destructuring dengan rest operator
let [first, ...rest] = [1, 2, 3, 4, 5];
console.log(first);  // 1
console.log(rest);   // [2, 3, 4, 5]

// ✅ Nested destructuring
let matrix = [[1, 2], [3, 4]];
let [[a, b], [c, d]] = matrix;
```

### 🔄 Spread Operator
```javascript
// ✅ Copy array
let original = [1, 2, 3];
let copy = [...original];

// ✅ Combine arrays
let arr1 = [1, 2];
let arr2 = [3, 4];
let combined = [...arr1, ...arr2];

// ✅ Add elements
let fruits = ["Apel", "Jeruk"];
let newFruits = [...fruits, "Mangga"];

// ✅ Spread dalam function arguments
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

let numbers = [1, 2, 3, 4, 5];
console.log(sum(...numbers));  // 15
```

### 🔄 Array-like Objects
```javascript
// ✅ Convert array-like objects to array
let arrayLike = { 0: "a", 1: "b", length: 2 };
let realArray = Array.from(arrayLike);

// ✅ Convert NodeList to array
let nodeList = document.querySelectorAll("div");
let divArray = Array.from(nodeList);

// ✅ Convert arguments object
function processArgs() {
    let args = Array.from(arguments);
    return args.map(arg => arg.toUpperCase());
}
```

---

> **💡 Pro Tip**: Array adalah struktur data paling fundamental dalam programming. Kuasai array methods dan patterns untuk menjadi developer yang efisien! 