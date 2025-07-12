# ⚙️ Functions Fundamental

## 1. Apa itu Function?

**Function** adalah blok kode yang dapat dipanggil dan digunakan kembali. Bayangkan function seperti resep masakan - Anda menulis resep sekali, kemudian bisa menggunakannya berulang kali dengan bahan yang berbeda.

### 🎯 Konsep Dasar
- **Reusability**: Kode dapat digunakan berulang kali
- **Modularity**: Memecah program menjadi bagian-bagian kecil
- **Abstraction**: Menyembunyikan kompleksitas implementasi
- **Parameters**: Input yang dapat diterima function
- **Return Value**: Output yang dihasilkan function

### 📝 Contoh Sederhana
```javascript
// Function sederhana
function greetUser() {
    console.log("Hello, welcome!");
}

// Function dengan parameter
function greetUserByName(name) {
    console.log(`Hello, ${name}!`);
}

// Function dengan return value
function calculateArea(length, width) {
    return length * width;
}

// Menggunakan function
greetUser();                    // "Hello, welcome!"
greetUserByName("Budi");        // "Hello, Budi!"
let area = calculateArea(5, 3); // 15
```

### 🔍 Istilah Penting
- **Function Declaration**: Cara mendeklarasikan function
- **Function Expression**: Function yang disimpan dalam variabel
- **Arrow Function**: Syntax modern untuk function
- **Parameter**: Variabel yang menerima input
- **Argument**: Nilai yang dikirim ke parameter
- **Return Statement**: Mengembalikan nilai dari function

## 2. Deklarasi Function

### 🔧 Function Declaration
```javascript
// ✅ Traditional function declaration
function calculateSum(a, b) {
    return a + b;
}

// ✅ Function dengan default parameter
function greetUser(name = "Guest") {
    return `Hello, ${name}!`;
}

// ✅ Function dengan multiple parameters
function createUser(firstName, lastName, age, email) {
    return {
        firstName,
        lastName,
        age,
        email,
        fullName: `${firstName} ${lastName}`
    };
}
```

### 🎯 Function Expression
```javascript
// ✅ Function expression
const multiply = function(a, b) {
    return a * b;
};

// ✅ Function expression dengan default parameter
const divide = function(a, b = 1) {
    return a / b;
};

// ✅ Function expression dalam object
const calculator = {
    add: function(a, b) {
        return a + b;
    },
    subtract: function(a, b) {
        return a - b;
    }
};
```

### ➡️ Arrow Function (ES6+)
```javascript
// ✅ Arrow function sederhana
const greet = (name) => `Hello, ${name}!`;

// ✅ Arrow function dengan multiple parameters
const calculateArea = (length, width) => length * width;

// ✅ Arrow function dengan block body
const processUser = (user) => {
    const { name, age } = user;
    return {
        name: name.toUpperCase(),
        age: age + 1,
        status: age >= 18 ? 'adult' : 'minor'
    };
};

// ✅ Arrow function tanpa parameter
const getRandomNumber = () => Math.random();
```

### 👻 Anonymous Function
```javascript
// ✅ Anonymous function sebagai callback
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(function(num) {
    return num * 2;
});

// ✅ Anonymous arrow function
const squared = numbers.map(num => num * num);

// ✅ Anonymous function sebagai event handler
button.addEventListener('click', function() {
    console.log('Button clicked!');
});
```

## 3. Parameter dan Arguments

### 📥 Parameter vs Arguments
```javascript
// Parameter adalah variabel dalam definisi function
function greetUser(name, age) {  // name, age adalah parameters
    console.log(`Hello ${name}, you are ${age} years old`);
}

// Arguments adalah nilai yang dikirim saat memanggil function
greetUser("Budi", 25);  // "Budi", 25 adalah arguments
```

### 🎯 Default Parameters
```javascript
// ✅ Default parameter sederhana
function greetUser(name = "Guest") {
    return `Hello, ${name}!`;
}

// ✅ Multiple default parameters
function createProfile(name = "Anonymous", age = 0, city = "Unknown") {
    return { name, age, city };
}

// ✅ Default parameter dengan expression
function calculateDiscount(price, discount = 0.1, tax = 0.05) {
    const discountedPrice = price * (1 - discount);
    return discountedPrice * (1 + tax);
}

// ✅ Default parameter menggunakan function
function getCurrentYear() {
    return new Date().getFullYear();
}

function calculateAge(birthYear, currentYear = getCurrentYear()) {
    return currentYear - birthYear;
}
```

### 📦 Rest Parameters
```javascript
// ✅ Rest parameter untuk multiple arguments
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5));  // 15

// ✅ Rest parameter dengan regular parameters
function createUser(name, email, ...hobbies) {
    return {
        name,
        email,
        hobbies: hobbies.length > 0 ? hobbies : ['reading']
    };
}

const user = createUser("Budi", "budi@email.com", "coding", "gaming", "music");
// { name: "Budi", email: "budi@email.com", hobbies: ["coding", "gaming", "music"] }
```

### 🔗 Parameter Destructuring
```javascript
// ✅ Object destructuring dalam parameter
function processUser({ name, age, email }) {
    return `User ${name} (${age}) - ${email}`;
}

const user = { name: "Budi", age: 25, email: "budi@email.com" };
console.log(processUser(user));  // "User Budi (25) - budi@email.com"

// ✅ Array destructuring dalam parameter
function processCoordinates([x, y, z = 0]) {
    return `Position: (${x}, ${y}, ${z})`;
}

console.log(processCoordinates([10, 20]));  // "Position: (10, 20, 0)"

// ✅ Nested destructuring
function processConfig({ api: { baseUrl, timeout = 5000 }, features }) {
    return {
        url: baseUrl,
        timeout,
        enabledFeatures: features.filter(f => f.enabled)
    };
}
```

## 4. Return Value

### 🔄 Return Statement
```javascript
// ✅ Explicit return
function add(a, b) {
    return a + b;
}

// ✅ Implicit return (arrow function)
const multiply = (a, b) => a * b;

// ✅ Early return pattern
function validateUser(user) {
    if (!user.name) {
        return { valid: false, error: "Name is required" };
    }
    
    if (!user.email) {
        return { valid: false, error: "Email is required" };
    }
    
    return { valid: true, user };
}

// ✅ Multiple return values (using object)
function divideWithRemainder(a, b) {
    if (b === 0) {
        return { error: "Division by zero" };
    }
    
    return {
        quotient: Math.floor(a / b),
        remainder: a % b
    };
}
```

### 🎭 Return Types
```javascript
// ✅ Returning primitive values
function getGreeting() {
    return "Hello, World!";
}

function getAge() {
    return 25;
}

function isAdult(age) {
    return age >= 18;
}

// ✅ Returning objects
function createUser(name, age) {
    return {
        id: Date.now(),
        name,
        age,
        isAdult: age >= 18
    };
}

// ✅ Returning arrays
function getEvenNumbers(max) {
    const evens = [];
    for (let i = 2; i <= max; i += 2) {
        evens.push(i);
    }
    return evens;
}

// ✅ Returning functions (Higher-order function)
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5));  // 10
console.log(triple(5));  // 15
```

### 🔄 Function Chaining
```javascript
// ✅ Method chaining dengan return this
const calculator = {
    value: 0,
    
    add(num) {
        this.value += num;
        return this;
    },
    
    subtract(num) {
        this.value -= num;
        return this;
    },
    
    multiply(num) {
        this.value *= num;
        return this;
    },
    
    getResult() {
        return this.value;
    }
};

const result = calculator
    .add(10)
    .multiply(2)
    .subtract(5)
    .getResult();  // 15
```

## 5. Function Scope

### 🏠 Local Scope
```javascript
// ✅ Variables dalam function hanya bisa diakses di dalam function
function testFunction() {
    let localVar = "I'm local";
    console.log(localVar);  // ✅ Bisa diakses
}

// console.log(localVar);  // ❌ Error - tidak bisa diakses di luar

// ✅ Function dapat mengakses variabel global
let globalVar = "I'm global";

function accessGlobal() {
    console.log(globalVar);  // ✅ Bisa mengakses global variable
}
```

### 🔒 Closure Concept
```javascript
// ✅ Closure - function yang mengingat environment di mana ia dibuat
function createCounter() {
    let count = 0;
    
    return function() {
        count++;
        return count;
    };
}

const counter1 = createCounter();
const counter2 = createCounter();

console.log(counter1());  // 1
console.log(counter1());  // 2
console.log(counter2());  // 1 (terpisah dari counter1)

// ✅ Closure dengan parameter
function createGreeter(greeting) {
    return function(name) {
        return `${greeting}, ${name}!`;
    };
}

const sayHello = createGreeter("Hello");
const sayHi = createGreeter("Hi");

console.log(sayHello("Budi"));  // "Hello, Budi!"
console.log(sayHi("Budi"));     // "Hi, Budi!"
```

### 🌍 Lexical Scoping
```javascript
// ✅ Lexical scoping - function mencari variabel di scope terdekat
let globalVar = "Global";

function outerFunction() {
    let outerVar = "Outer";
    
    function innerFunction() {
        let innerVar = "Inner";
        console.log(innerVar);   // "Inner"
        console.log(outerVar);   // "Outer"
        console.log(globalVar);  // "Global"
    }
    
    innerFunction();
}

outerFunction();
```

### 🔄 Global vs Function Scope
```javascript
// ✅ Global variable
let globalCounter = 0;

function incrementGlobal() {
    globalCounter++;
    return globalCounter;
}

// ✅ Local variable (shadowing global)
function createLocalCounter() {
    let localCounter = 0;
    
    return function() {
        localCounter++;
        return localCounter;
    };
}

const localCounter = createLocalCounter();

console.log(incrementGlobal());  // 1
console.log(incrementGlobal());  // 2
console.log(localCounter());     // 1 (terpisah)
console.log(localCounter());     // 2
```

## 6. Function Types

### 🎯 Pure Functions
```javascript
// ✅ Pure function - selalu return nilai yang sama untuk input yang sama
function add(a, b) {
    return a + b;
}

function multiply(a, b) {
    return a * b;
}

function createFullName(firstName, lastName) {
    return `${firstName} ${lastName}`;
}

// ✅ Pure function dengan object
function updateUserAge(user, newAge) {
    return {
        ...user,
        age: newAge
    };
}

const user = { name: "Budi", age: 25 };
const updatedUser = updateUserAge(user, 26);
// user tidak berubah, updatedUser adalah object baru
```

### 🎭 Impure Functions
```javascript
// ❌ Impure function - mengubah state eksternal
let counter = 0;

function incrementCounter() {
    counter++;
    return counter;
}

// ❌ Impure function - bergantung pada external state
function getCurrentTime() {
    return new Date().toLocaleTimeString();
}

// ❌ Impure function - side effects
function logUser(user) {
    console.log(`User: ${user.name}`);
    // Side effect: console.log
}
```

### 🔄 Higher-Order Functions
```javascript
// ✅ Function yang menerima function sebagai parameter
function processArray(array, processor) {
    return array.map(processor);
}

const numbers = [1, 2, 3, 4, 5];
const doubled = processArray(numbers, num => num * 2);
const squared = processArray(numbers, num => num * num);

// ✅ Function yang return function
function createValidator(rule) {
    return function(value) {
        return rule(value);
    };
}

const isPositive = createValidator(value => value > 0);
const isEven = createValidator(value => value % 2 === 0);

console.log(isPositive(5));  // true
console.log(isEven(4));      // true
```

### 📞 Callback Functions
```javascript
// ✅ Callback function untuk event handling
function handleClick(event) {
    console.log('Button clicked!');
    console.log('Event:', event);
}

// button.addEventListener('click', handleClick);

// ✅ Callback function untuk array methods
const users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 },
    { name: "Charlie", age: 22 }
];

const adultUsers = users.filter(user => user.age >= 18);
const userNames = users.map(user => user.name);
const totalAge = users.reduce((sum, user) => sum + user.age, 0);

// ✅ Callback function untuk async operations
function fetchUserData(userId, callback) {
    setTimeout(() => {
        const user = { id: userId, name: "Budi", age: 25 };
        callback(user);
    }, 1000);
}

fetchUserData(123, function(user) {
    console.log('User data:', user);
});
```

## 7. Best Practices & Patterns

### 🛡️ Defensive Programming
```javascript
// ✅ Validasi parameter
function calculateArea(length, width) {
    if (typeof length !== 'number' || typeof width !== 'number') {
        throw new Error('Length and width must be numbers');
    }
    
    if (length <= 0 || width <= 0) {
        throw new Error('Length and width must be positive');
    }
    
    return length * width;
}

// ✅ Default values
function createUser(name, age = 0, email = '') {
    return {
        name: name || 'Anonymous',
        age,
        email,
        isAdult: age >= 18
    };
}

// ✅ Error handling
function safeDivide(a, b) {
    try {
        if (b === 0) {
            throw new Error('Division by zero');
        }
        return a / b;
    } catch (error) {
        console.error('Error:', error.message);
        return null;
    }
}
```

### 🎯 Function Composition
```javascript
// ✅ Function composition - menggabungkan multiple functions
function compose(...functions) {
    return function(value) {
        return functions.reduceRight((result, fn) => fn(result), value);
    };
}

const addOne = x => x + 1;
const multiplyByTwo = x => x * 2;
const square = x => x * x;

const composed = compose(square, multiplyByTwo, addOne);
console.log(composed(3));  // ((3 + 1) * 2)² = 64

// ✅ Pipeline pattern
function pipeline(value, ...functions) {
    return functions.reduce((result, fn) => fn(result), value);
}

const result = pipeline(3, addOne, multiplyByTwo, square);
console.log(result);  // ((3 + 1) * 2)² = 64
```

### 🔄 Memoization Pattern
```javascript
// ✅ Memoization - cache hasil function
function memoize(fn) {
    const cache = new Map();
    
    return function(...args) {
        const key = JSON.stringify(args);
        
        if (cache.has(key)) {
            return cache.get(key);
        }
        
        const result = fn.apply(this, args);
        cache.set(key, result);
        return result;
    };
}

// ✅ Fibonacci dengan memoization
const fibonacci = memoize(function(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
});

console.log(fibonacci(10));  // 55 (dengan cache)
```

## 8. Studi Kasus Praktis

### 🛒 E-commerce System
```javascript
// ✅ Product management functions
const productCatalog = {
    products: [],
    
    addProduct(product) {
        if (!product.name || !product.price) {
            throw new Error('Product must have name and price');
        }
        
        const newProduct = {
            id: Date.now(),
            ...product,
            createdAt: new Date()
        };
        
        this.products.push(newProduct);
        return newProduct;
    },
    
    findProduct(id) {
        return this.products.find(product => product.id === id);
    },
    
    updateProduct(id, updates) {
        const index = this.products.findIndex(product => product.id === id);
        if (index === -1) {
            throw new Error('Product not found');
        }
        
        this.products[index] = { ...this.products[index], ...updates };
        return this.products[index];
    },
    
    deleteProduct(id) {
        const index = this.products.findIndex(product => product.id === id);
        if (index === -1) {
            throw new Error('Product not found');
        }
        
        return this.products.splice(index, 1)[0];
    }
};

// ✅ Order processing functions
function calculateOrderTotal(items, taxRate = 0.1) {
    const subtotal = items.reduce((sum, item) => sum + item.price * item.quantity, 0);
    const tax = subtotal * taxRate;
    return {
        subtotal,
        tax,
        total: subtotal + tax
    };
}

function validateOrder(order) {
    const errors = [];
    
    if (!order.customerId) {
        errors.push('Customer ID is required');
    }
    
    if (!order.items || order.items.length === 0) {
        errors.push('Order must have at least one item');
    }
    
    if (order.items) {
        order.items.forEach((item, index) => {
            if (!item.productId) {
                errors.push(`Item ${index + 1}: Product ID is required`);
            }
            if (!item.quantity || item.quantity <= 0) {
                errors.push(`Item ${index + 1}: Valid quantity is required`);
            }
        });
    }
    
    return {
        isValid: errors.length === 0,
        errors
    };
}
```

### 🎮 Game Development
```javascript
// ✅ Game state management
class GameEngine {
    constructor() {
        this.state = {
            player: { x: 0, y: 0, health: 100, score: 0 },
            enemies: [],
            level: 1,
            isGameOver: false
        };
    }
    
    updatePlayerPosition(dx, dy) {
        if (this.state.isGameOver) return;
        
        this.state.player.x += dx;
        this.state.player.y += dy;
        
        // Boundary checking
        this.state.player.x = Math.max(0, Math.min(800, this.state.player.x));
        this.state.player.y = Math.max(0, Math.min(600, this.state.player.y));
    }
    
    spawnEnemy() {
        const enemy = {
            id: Date.now(),
            x: Math.random() * 800,
            y: Math.random() * 600,
            health: 50
        };
        
        this.state.enemies.push(enemy);
    }
    
    attackEnemy(enemyId) {
        const enemy = this.state.enemies.find(e => e.id === enemyId);
        if (!enemy) return false;
        
        enemy.health -= 25;
        if (enemy.health <= 0) {
            this.state.enemies = this.state.enemies.filter(e => e.id !== enemyId);
            this.state.player.score += 100;
        }
        
        return true;
    }
    
    getGameState() {
        return { ...this.state };
    }
}

// ✅ Utility functions
function calculateDistance(point1, point2) {
    const dx = point2.x - point1.x;
    const dy = point2.y - point1.y;
    return Math.sqrt(dx * dx + dy * dy);
}

function isColliding(rect1, rect2) {
    return rect1.x < rect2.x + rect2.width &&
           rect1.x + rect1.width > rect2.x &&
           rect1.y < rect2.y + rect2.height &&
           rect1.y + rect1.height > rect2.y;
}
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- **JavaScript.info**: [Functions](https://javascript.info/function-basics)
- **Eloquent JavaScript**: [Functions Chapter](https://eloquentjavascript.net/03_functions.html)

### 📖 Buku Rekomendasi
- "Functional Programming in JavaScript" by Luis Atencio
- "JavaScript: The Good Parts" by Douglas Crockford
- "You Don't Know JS: Scope & Closures" by Kyle Simpson

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Functions Tutorial
- **The Net Ninja**: JavaScript Functions & Scope
- **Programming with Mosh**: JavaScript Functions

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen function
- **JSFiddle**: Untuk testing function
- **Replit**: Untuk project function
- **LeetCode**: Untuk latihan algoritma dengan function

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan function sederhana
2. **Practice Parameters**: Latihan dengan berbagai jenis parameter
3. **Master Return Values**: Pahami cara return yang benar
4. **Learn Scope**: Kuasai konsep scope dan closure
5. **Build Projects**: Aplikasikan dalam project nyata

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep function
2. **Practice** → Tulis function dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki function
5. **Repeat** → Ulangi dengan konsep function baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Functions
- **freeCodeCamp**: JavaScript Functions and Scope
- **Scrimba**: Function tutorials
- **JavaScript30**: Function-based challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Function hoisting confusion
sayHello();  // Error jika menggunakan function expression
const sayHello = () => console.log("Hello");

// ✅ Solusi: Gunakan function declaration atau pindahkan ke atas
function sayHello() {
    console.log("Hello");
}
sayHello();  // ✅ Works

// ❌ Parameter mutation
function updateUser(user) {
    user.age = 26;  // ❌ Mutasi parameter
    return user;
}

// ✅ Solusi: Buat copy baru
function updateUser(user) {
    return { ...user, age: 26 };  // ✅ Immutable
}

// ❌ Missing return statement
function calculateSum(a, b) {
    a + b;  // ❌ Tidak ada return
}

// ✅ Solusi: Tambahkan return
function calculateSum(a, b) {
    return a + b;  // ✅ Ada return
}
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.log untuk debugging function
function debugFunction(a, b) {
    console.log('Input:', { a, b });
    const result = a + b;
    console.log('Result:', result);
    return result;
}

// ✅ Gunakan debugger statement
function complexFunction(data) {
    debugger;  // Browser akan pause di sini
    // Process data
    return processedData;
}

// ✅ Gunakan function name untuk debugging
const namedFunction = function processData(data) {
    // Function name akan muncul di stack trace
    return data.map(item => item * 2);
};
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Function Currying
```javascript
// ✅ Currying - mengubah function multi-parameter menjadi chain
function curry(fn) {
    return function curried(...args) {
        if (args.length >= fn.length) {
            return fn.apply(this, args);
        }
        return function(...moreArgs) {
            return curried.apply(this, args.concat(moreArgs));
        };
    };
}

const add = curry((a, b, c) => a + b + c);
const add5 = add(5);
const add5And3 = add5(3);
console.log(add5And3(2));  // 10
```

### 🎭 Partial Application
```javascript
// ✅ Partial application - mengisi beberapa parameter
function partial(fn, ...presetArgs) {
    return function(...laterArgs) {
        return fn.apply(this, presetArgs.concat(laterArgs));
    };
}

function greet(greeting, name) {
    return `${greeting}, ${name}!`;
}

const sayHello = partial(greet, "Hello");
console.log(sayHello("Budi"));  // "Hello, Budi!"
```

### 🔗 Function Composition
```javascript
// ✅ Function composition utility
const compose = (...fns) => x => fns.reduceRight((y, f) => f(y), x);
const pipe = (...fns) => x => fns.reduce((y, f) => f(y), x);

const addOne = x => x + 1;
const double = x => x * 2;
const square = x => x * x;

const composed = compose(square, double, addOne);
const piped = pipe(addOne, double, square);

console.log(composed(3));  // ((3 + 1) * 2)² = 64
console.log(piped(3));     // ((3 + 1) * 2)² = 64
```

---

> **💡 Pro Tip**: Function adalah jantung programming. Kuasai konsep ini dengan baik untuk menjadi developer yang handal. Practice, practice, practice! 