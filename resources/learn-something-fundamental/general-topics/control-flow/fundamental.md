# 🔄 Control Flow Fundamental

## 1. Apa itu Control Flow?

**Control Flow** adalah cara mengontrol alur eksekusi program berdasarkan kondisi tertentu. Bayangkan seperti rambu lalu lintas - program akan mengambil jalan yang berbeda tergantung pada kondisi yang ada.

### 🎯 Konsep Dasar
- **Conditional**: Membuat keputusan berdasarkan kondisi
- **Looping**: Mengulang kode berdasarkan kondisi
- **Branching**: Memilih jalur eksekusi yang berbeda
- **Sequential**: Eksekusi kode secara berurutan
- **Nested**: Kondisi di dalam kondisi

### 📝 Contoh Sederhana
```javascript
// Conditional statement
let age = 18;
if (age >= 18) {
    console.log("Anda sudah dewasa");
} else {
    console.log("Anda masih di bawah umur");
}

// Loop statement
for (let i = 1; i <= 5; i++) {
    console.log(`Angka ke-${i}`);
}

// Switch statement
let day = "Senin";
switch (day) {
    case "Senin":
        console.log("Hari kerja");
        break;
    case "Sabtu":
    case "Minggu":
        console.log("Hari libur");
        break;
    default:
        console.log("Hari biasa");
}
```

### 🔍 Istilah Penting
- **Condition**: Ekspresi yang menghasilkan true/false
- **Statement**: Instruksi yang dapat dieksekusi
- **Block**: Kumpulan statement dalam kurung kurawal {}
- **Expression**: Kode yang menghasilkan nilai
- **Operator**: Simbol untuk operasi tertentu

## 2. Conditional Statements

### 🔍 If Statement
```javascript
// ✅ Basic if statement
let age = 18;
if (age >= 18) {
    console.log("Anda sudah dewasa");
}

// ✅ If dengan block statement
let score = 85;
if (score >= 90) {
    console.log("Grade A");
    console.log("Excellent!");
}

// ✅ If dengan single statement (tanpa kurung kurawal)
let isLoggedIn = true;
if (isLoggedIn) console.log("Welcome back!");

// ✅ If dengan multiple conditions
let userAge = 25;
let hasPermission = true;

if (userAge >= 18 && hasPermission) {
    console.log("Access granted");
}
```

### 🔄 If-Else Statement
```javascript
// ✅ Basic if-else
let temperature = 25;
if (temperature > 30) {
    console.log("Panas sekali!");
} else {
    console.log("Suhu normal");
}

// ✅ If-else dengan multiple conditions
let grade = 85;
if (grade >= 90) {
    console.log("Grade A");
} else if (grade >= 80) {
    console.log("Grade B");
} else if (grade >= 70) {
    console.log("Grade C");
} else {
    console.log("Grade D");
}

// ✅ Nested if-else
let userType = "admin";
let isActive = true;

if (userType === "admin") {
    if (isActive) {
        console.log("Admin aktif");
    } else {
        console.log("Admin tidak aktif");
    }
} else {
    console.log("User biasa");
}
```

### 🎯 Ternary Operator
```javascript
// ✅ Basic ternary operator
let age = 18;
let status = age >= 18 ? "Dewasa" : "Anak-anak";
console.log(status);  // "Dewasa"

// ✅ Ternary dengan multiple conditions
let score = 85;
let grade = score >= 90 ? "A" : 
           score >= 80 ? "B" : 
           score >= 70 ? "C" : "D";

// ✅ Ternary untuk assignment
let userRole = "admin";
let canAccess = userRole === "admin" ? true : false;

// ✅ Ternary untuk function call
let isLoggedIn = true;
isLoggedIn ? showDashboard() : showLoginForm();

// ✅ Ternary dengan object
let theme = "dark";
let colors = theme === "dark" ? 
    { bg: "#000", text: "#fff" } : 
    { bg: "#fff", text: "#000" };
```

### 🔍 Truthy dan Falsy Values
```javascript
// ✅ Falsy values di JavaScript
let falsyValues = [false, 0, "", null, undefined, NaN];

// ✅ Truthy values
let truthyValues = [true, 1, "hello", [], {}, function(){}];

// ✅ Checking truthy/falsy
function checkValue(value) {
    if (value) {
        console.log(`${value} is truthy`);
    } else {
        console.log(`${value} is falsy`);
    }
}

// ✅ Short-circuit evaluation
let user = null;
let userName = user && user.name;  // null (short-circuit)
let defaultName = user || "Guest"; // "Guest"

// ✅ Nullish coalescing (??)
let count = 0;
let displayCount = count || "No items";  // "No items" (0 is falsy)
let displayCount2 = count ?? "No items"; // 0 (nullish coalescing)
```

## 3. Switch Case

### 🔄 Basic Switch Statement
```javascript
// ✅ Basic switch case
let day = "Senin";
switch (day) {
    case "Senin":
        console.log("Hari kerja");
        break;
    case "Selasa":
        console.log("Hari kerja");
        break;
    case "Sabtu":
    case "Minggu":
        console.log("Hari libur");
        break;
    default:
        console.log("Hari tidak dikenal");
}

// ✅ Switch dengan expression
let score = 85;
switch (true) {
    case score >= 90:
        console.log("Grade A");
        break;
    case score >= 80:
        console.log("Grade B");
        break;
    case score >= 70:
        console.log("Grade C");
        break;
    default:
        console.log("Grade D");
}
```

### ⚠️ Break Statement
```javascript
// ✅ Switch dengan break
let fruit = "Apel";
switch (fruit) {
    case "Apel":
        console.log("Buah merah");
        break;  // Penting! Tanpa break akan fall-through
    case "Jeruk":
        console.log("Buah oranye");
        break;
    default:
        console.log("Buah tidak dikenal");
}

// ✅ Intentional fall-through
let month = 2;
switch (month) {
    case 12:
    case 1:
    case 2:
        console.log("Musim dingin");
        break;
    case 3:
    case 4:
    case 5:
        console.log("Musim semi");
        break;
    default:
        console.log("Musim lainnya");
}
```

### 🎯 Switch dengan Return
```javascript
// ✅ Switch dalam function
function getDayType(day) {
    switch (day.toLowerCase()) {
        case "senin":
        case "selasa":
        case "rabu":
        case "kamis":
        case "jumat":
            return "Hari kerja";
        case "sabtu":
        case "minggu":
            return "Hari libur";
        default:
            return "Hari tidak valid";
    }
}

// ✅ Switch dengan object mapping
function getGrade(score) {
    switch (true) {
        case score >= 90:
            return { grade: "A", description: "Excellent" };
        case score >= 80:
            return { grade: "B", description: "Good" };
        case score >= 70:
            return { grade: "C", description: "Average" };
        default:
            return { grade: "D", description: "Poor" };
    }
}
```

## 4. Loops

### 🔄 For Loop
```javascript
// ✅ Basic for loop
for (let i = 0; i < 5; i++) {
    console.log(`Iterasi ke-${i}`);
}

// ✅ For loop dengan array
let fruits = ["Apel", "Jeruk", "Mangga"];
for (let i = 0; i < fruits.length; i++) {
    console.log(`Buah ke-${i + 1}: ${fruits[i]}`);
}

// ✅ For loop dengan step
for (let i = 0; i <= 10; i += 2) {
    console.log(`Angka genap: ${i}`);
}

// ✅ For loop dengan decrement
for (let i = 10; i >= 0; i--) {
    console.log(`Countdown: ${i}`);
}

// ✅ Nested for loop
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(`i=${i}, j=${j}`);
    }
}
```

### 🔄 While Loop
```javascript
// ✅ Basic while loop
let count = 0;
while (count < 5) {
    console.log(`Count: ${count}`);
    count++;
}

// ✅ While loop dengan condition
let password = "";
while (password.length < 8) {
    password += "a";
    console.log(`Password: ${password}`);
}

// ✅ While loop dengan break
let number = 1;
while (true) {
    if (number > 10) {
        break;
    }
    console.log(number);
    number++;
}

// ✅ While loop dengan continue
let i = 0;
while (i < 10) {
    i++;
    if (i % 2 === 0) {
        continue;  // Skip angka genap
    }
    console.log(`Angka ganjil: ${i}`);
}
```

### 🔄 Do-While Loop
```javascript
// ✅ Basic do-while loop
let counter = 0;
do {
    console.log(`Counter: ${counter}`);
    counter++;
} while (counter < 5);

// ✅ Do-while dengan condition yang false
let x = 10;
do {
    console.log("Ini akan dieksekusi sekali");
} while (x < 5);  // Condition false, tapi loop tetap jalan sekali

// ✅ Do-while untuk input validation
let userInput;
do {
    userInput = prompt("Masukkan angka 1-10:");
} while (userInput < 1 || userInput > 10);
```

### 🔄 For-In Loop
```javascript
// ✅ For-in dengan object
let person = { name: "Budi", age: 25, city: "Jakarta" };
for (let key in person) {
    console.log(`${key}: ${person[key]}`);
}

// ✅ For-in dengan array (tidak direkomendasikan)
let fruits = ["Apel", "Jeruk", "Mangga"];
for (let index in fruits) {
    console.log(`Index ${index}: ${fruits[index]}`);
}

// ✅ For-in dengan prototype properties
Array.prototype.customMethod = function() {};
for (let prop in fruits) {
    console.log(prop);  // Akan include "customMethod"
}
```

### 🔄 For-Of Loop (ES6+)
```javascript
// ✅ For-of dengan array
let fruits = ["Apel", "Jeruk", "Mangga"];
for (let fruit of fruits) {
    console.log(fruit);
}

// ✅ For-of dengan string
let text = "Hello";
for (let char of text) {
    console.log(char);
}

// ✅ For-of dengan Set
let uniqueNumbers = new Set([1, 2, 2, 3, 3, 4]);
for (let num of uniqueNumbers) {
    console.log(num);
}

// ✅ For-of dengan Map
let userMap = new Map([
    ["name", "Budi"],
    ["age", 25]
]);
for (let [key, value] of userMap) {
    console.log(`${key}: ${value}`);
}
```

## 5. Loop Control

### 🛑 Break Statement
```javascript
// ✅ Break dalam for loop
for (let i = 1; i <= 10; i++) {
    if (i === 5) {
        break;  // Keluar dari loop
    }
    console.log(i);
}

// ✅ Break dalam while loop
let number = 1;
while (true) {
    if (number > 5) {
        break;
    }
    console.log(number);
    number++;
}

// ✅ Break dalam nested loop
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        if (i === 2 && j === 2) {
            break;  // Hanya keluar dari inner loop
        }
        console.log(`i=${i}, j=${j}`);
    }
}
```

### ⏭️ Continue Statement
```javascript
// ✅ Continue dalam for loop
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue;  // Skip angka genap
    }
    console.log(`Angka ganjil: ${i}`);
}

// ✅ Continue dalam while loop
let count = 0;
while (count < 10) {
    count++;
    if (count === 5) {
        continue;  // Skip angka 5
    }
    console.log(count);
}

// ✅ Continue dengan nested loop
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        if (i === j) {
            continue;  // Skip diagonal
        }
        console.log(`i=${i}, j=${j}`);
    }
}
```

### 🏷️ Labeled Statements
```javascript
// ✅ Labeled break
outerLoop: for (let i = 1; i <= 3; i++) {
    innerLoop: for (let j = 1; j <= 3; j++) {
        if (i === 2 && j === 2) {
            break outerLoop;  // Keluar dari kedua loop
        }
        console.log(`i=${i}, j=${j}`);
    }
}

// ✅ Labeled continue
outer: for (let i = 1; i <= 3; i++) {
    inner: for (let j = 1; j <= 3; j++) {
        if (i === j) {
            continue outer;  // Lanjut ke iterasi berikutnya di outer loop
        }
        console.log(`i=${i}, j=${j}`);
    }
}
```

### 🔄 Nested Loops
```javascript
// ✅ Nested for loops
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(`(${i}, ${j})`);
    }
}

// ✅ Nested loops dengan different types
let users = [
    { name: "Budi", hobbies: ["coding", "gaming"] },
    { name: "Ani", hobbies: ["reading", "cooking"] }
];

for (let user of users) {
    console.log(`User: ${user.name}`);
    for (let hobby of user.hobbies) {
        console.log(`  - ${hobby}`);
    }
}

// ✅ Nested loops dengan condition
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

for (let i = 0; i < matrix.length; i++) {
    for (let j = 0; j < matrix[i].length; j++) {
        if (matrix[i][j] % 2 === 0) {
            console.log(`Even number at [${i}][${j}]: ${matrix[i][j]}`);
        }
    }
}
```

## 6. Logical Operators

### 🔗 AND Operator (&&)
```javascript
// ✅ Basic AND operator
let age = 25;
let hasPermission = true;

if (age >= 18 && hasPermission) {
    console.log("Access granted");
}

// ✅ Short-circuit evaluation
let user = null;
let userName = user && user.name;  // null (short-circuit)

// ✅ Multiple conditions
let score = 85;
let attendance = 90;
let participation = true;

if (score >= 80 && attendance >= 85 && participation) {
    console.log("Student eligible for honors");
}

// ✅ AND dengan function calls
function checkAge(age) {
    console.log("Checking age...");
    return age >= 18;
}

function checkPermission(hasPermission) {
    console.log("Checking permission...");
    return hasPermission;
}

// Hanya checkAge yang dieksekusi karena short-circuit
if (checkAge(16) && checkPermission(true)) {
    console.log("Access granted");
}
```

### 🔗 OR Operator (||)
```javascript
// ✅ Basic OR operator
let userRole = "admin";
let isSuperUser = false;

if (userRole === "admin" || isSuperUser) {
    console.log("Access granted");
}

// ✅ Default values
let userName = user.name || "Guest";
let port = process.env.PORT || 3000;

// ✅ Multiple OR conditions
let day = "Sabtu";
if (day === "Sabtu" || day === "Minggu") {
    console.log("Weekend!");
}

// ✅ OR dengan function calls
function getDefaultTheme() {
    console.log("Getting default theme...");
    return "light";
}

let theme = userPreference || getDefaultTheme();
```

### 🔗 NOT Operator (!)
```javascript
// ✅ Basic NOT operator
let isLoggedIn = false;
if (!isLoggedIn) {
    console.log("Please log in");
}

// ✅ NOT dengan comparison
let age = 16;
if (!(age >= 18)) {
    console.log("Too young");
}

// ✅ NOT dengan multiple conditions
let hasPermission = false;
let isAdmin = false;

if (!hasPermission && !isAdmin) {
    console.log("Access denied");
}

// ✅ Double negation
let value = "hello";
let isTruthy = !!value;  // true
```

### 🔗 Short-Circuit Evaluation
```javascript
// ✅ AND short-circuit
let user = null;
let result = user && user.name;  // null (tidak dievaluasi user.name)

// ✅ OR short-circuit
let config = process.env.CONFIG || "default";

// ✅ Chaining short-circuit
let value = obj && obj.prop && obj.prop.subProp;

// ✅ Function calls dengan short-circuit
function expensiveOperation() {
    console.log("Expensive operation...");
    return true;
}

let shouldRun = false;
// expensiveOperation tidak akan dipanggil
if (shouldRun && expensiveOperation()) {
    console.log("Operation completed");
}
```

## 7. Best Practices & Patterns

### 🛡️ Defensive Programming
```javascript
// ✅ Validasi input
function processUser(user) {
    if (!user) {
        throw new Error("User is required");
    }
    
    if (!user.name || typeof user.name !== 'string') {
        throw new Error("Valid name is required");
    }
    
    if (!user.age || user.age < 0) {
        throw new Error("Valid age is required");
    }
    
    return `Hello, ${user.name}! You are ${user.age} years old.`;
}

// ✅ Safe property access
function getUserName(user) {
    return user && user.name || "Anonymous";
}

// ✅ Default values
function createConfig(options = {}) {
    return {
        port: options.port || 3000,
        host: options.host || "localhost",
        debug: options.debug || false
    };
}
```

### 🎯 Early Return Pattern
```javascript
// ✅ Early return untuk validasi
function validateUser(user) {
    if (!user) {
        return { valid: false, error: "User is required" };
    }
    
    if (!user.name) {
        return { valid: false, error: "Name is required" };
    }
    
    if (!user.email) {
        return { valid: false, error: "Email is required" };
    }
    
    return { valid: true, user };
}

// ✅ Early return untuk performance
function findUser(users, id) {
    if (!users || users.length === 0) {
        return null;
    }
    
    if (!id) {
        return null;
    }
    
    for (let user of users) {
        if (user.id === id) {
            return user;
        }
    }
    
    return null;
}
```

### 🔄 Guard Clauses
```javascript
// ✅ Guard clauses untuk nested conditions
function processOrder(order) {
    // Guard clause 1
    if (!order) {
        return { success: false, error: "Order is required" };
    }
    
    // Guard clause 2
    if (!order.items || order.items.length === 0) {
        return { success: false, error: "Order must have items" };
    }
    
    // Guard clause 3
    if (!order.customerId) {
        return { success: false, error: "Customer ID is required" };
    }
    
    // Main logic
    const total = order.items.reduce((sum, item) => sum + item.price, 0);
    return { success: true, total };
}
```

## 8. Studi Kasus Praktis

### 🛒 E-commerce Order Processing
```javascript
// ✅ Order validation system
function validateOrder(order) {
    // Guard clauses
    if (!order) {
        return { valid: false, error: "Order is required" };
    }
    
    if (!order.customerId) {
        return { valid: false, error: "Customer ID is required" };
    }
    
    if (!order.items || order.items.length === 0) {
        return { valid: false, error: "Order must have at least one item" };
    }
    
    // Validate each item
    for (let i = 0; i < order.items.length; i++) {
        const item = order.items[i];
        
        if (!item.productId) {
            return { valid: false, error: `Item ${i + 1}: Product ID is required` };
        }
        
        if (!item.quantity || item.quantity <= 0) {
            return { valid: false, error: `Item ${i + 1}: Valid quantity is required` };
        }
        
        if (item.price < 0) {
            return { valid: false, error: `Item ${i + 1}: Price cannot be negative` };
        }
    }
    
    return { valid: true };
}

// ✅ Order processing with different statuses
function processOrder(order) {
    const validation = validateOrder(order);
    if (!validation.valid) {
        return { status: "rejected", error: validation.error };
    }
    
    // Calculate total
    const total = order.items.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    
    // Apply discount based on total
    let discount = 0;
    if (total >= 1000000) {
        discount = 0.1;  // 10% discount
    } else if (total >= 500000) {
        discount = 0.05; // 5% discount
    }
    
    const finalTotal = total * (1 - discount);
    
    return {
        status: "approved",
        total: total,
        discount: discount,
        finalTotal: finalTotal
    };
}
```

### 🎮 Game Logic System
```javascript
// ✅ Game state management
class GameEngine {
    constructor() {
        this.state = {
            player: { health: 100, level: 1, experience: 0 },
            enemies: [],
            gameOver: false
        };
    }
    
    updatePlayerHealth(damage) {
        if (this.state.gameOver) {
            return { success: false, message: "Game is over" };
        }
        
        this.state.player.health -= damage;
        
        if (this.state.player.health <= 0) {
            this.state.player.health = 0;
            this.state.gameOver = true;
            return { success: false, message: "Game Over!" };
        }
        
        return { success: true, health: this.state.player.health };
    }
    
    addExperience(exp) {
        if (this.state.gameOver) {
            return { success: false, message: "Game is over" };
        }
        
        this.state.player.experience += exp;
        
        // Level up logic
        const requiredExp = this.state.player.level * 100;
        if (this.state.player.experience >= requiredExp) {
            this.state.player.level++;
            this.state.player.experience -= requiredExp;
            this.state.player.health = Math.min(100, this.state.player.health + 20);
            
            return {
                success: true,
                levelUp: true,
                newLevel: this.state.player.level,
                health: this.state.player.health
            };
        }
        
        return { success: true, levelUp: false };
    }
    
    spawnEnemy() {
        if (this.state.gameOver) {
            return { success: false, message: "Game is over" };
        }
        
        const enemy = {
            id: Date.now(),
            health: 50,
            level: Math.floor(Math.random() * 3) + 1
        };
        
        this.state.enemies.push(enemy);
        return { success: true, enemy };
    }
    
    attackEnemy(enemyId, damage) {
        if (this.state.gameOver) {
            return { success: false, message: "Game is over" };
        }
        
        const enemy = this.state.enemies.find(e => e.id === enemyId);
        if (!enemy) {
            return { success: false, message: "Enemy not found" };
        }
        
        enemy.health -= damage;
        
        if (enemy.health <= 0) {
            // Remove enemy and give experience
            this.state.enemies = this.state.enemies.filter(e => e.id !== enemyId);
            const expGain = enemy.level * 10;
            this.addExperience(expGain);
            
            return {
                success: true,
                enemyDefeated: true,
                experienceGained: expGain
            };
        }
        
        return { success: true, enemyDefeated: false, enemyHealth: enemy.health };
    }
}
```

### 📊 Data Processing System
```javascript
// ✅ Data analysis with control flow
function analyzeSalesData(salesData) {
    if (!salesData || !Array.isArray(salesData)) {
        return { error: "Invalid data format" };
    }
    
    if (salesData.length === 0) {
        return { error: "No data to analyze" };
    }
    
    let totalSales = 0;
    let highestSale = 0;
    let lowestSale = Infinity;
    let salesByMonth = {};
    
    for (let sale of salesData) {
        // Validate sale data
        if (!sale.amount || sale.amount < 0) {
            continue; // Skip invalid data
        }
        
        totalSales += sale.amount;
        
        // Track highest and lowest
        if (sale.amount > highestSale) {
            highestSale = sale.amount;
        }
        
        if (sale.amount < lowestSale) {
            lowestSale = sale.amount;
        }
        
        // Group by month
        const month = sale.date ? new Date(sale.date).getMonth() : 'Unknown';
        salesByMonth[month] = (salesByMonth[month] || 0) + sale.amount;
    }
    
    const averageSale = totalSales / salesData.length;
    
    // Determine performance category
    let performance;
    if (averageSale >= 1000000) {
        performance = "Excellent";
    } else if (averageSale >= 500000) {
        performance = "Good";
    } else if (averageSale >= 100000) {
        performance = "Average";
    } else {
        performance = "Poor";
    }
    
    return {
        totalSales,
        averageSale,
        highestSale,
        lowestSale: lowestSale === Infinity ? 0 : lowestSale,
        salesByMonth,
        performance,
        dataPoints: salesData.length
    };
}

// ✅ Data filtering system
function filterData(data, filters) {
    if (!data || !Array.isArray(data)) {
        return [];
    }
    
    let filteredData = [...data];
    
    // Apply each filter
    for (let filter of filters) {
        switch (filter.type) {
            case "range":
                filteredData = filteredData.filter(item => 
                    item[filter.field] >= filter.min && 
                    item[filter.field] <= filter.max
                );
                break;
                
            case "equals":
                filteredData = filteredData.filter(item => 
                    item[filter.field] === filter.value
                );
                break;
                
            case "contains":
                filteredData = filteredData.filter(item => 
                    String(item[filter.field]).toLowerCase()
                        .includes(filter.value.toLowerCase())
                );
                break;
                
            case "custom":
                filteredData = filteredData.filter(filter.predicate);
                break;
        }
    }
    
    return filteredData;
}
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Control Flow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- **JavaScript.info**: [Conditional Branching](https://javascript.info/ifelse)
- **W3Schools**: [JavaScript If...Else](https://www.w3schools.com/js/js_if_else.asp)

### 📖 Buku Rekomendasi
- "Eloquent JavaScript" by Marijn Haverbeke
- "JavaScript: The Definitive Guide" by David Flanagan
- "You Don't Know JS: Scope & Closures" by Kyle Simpson

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Control Flow Tutorial
- **The Net Ninja**: JavaScript Loops & Conditionals
- **Programming with Mosh**: JavaScript Control Flow

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen control flow
- **JSFiddle**: Untuk testing conditions dan loops
- **Replit**: Untuk project control flow
- **LeetCode**: Untuk latihan algoritma dengan control flow

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan if-else sederhana
2. **Learn Loops**: Kuasai berbagai jenis loop
3. **Practice Conditions**: Latihan dengan kondisi kompleks
4. **Build Projects**: Aplikasikan dalam project nyata
5. **Optimize**: Pelajari best practices dan patterns

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep control flow
2. **Practice** → Tulis kode dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki
5. **Repeat** → Ulangi dengan konsep control flow baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Control Flow
- **freeCodeCamp**: JavaScript Loops and Conditionals
- **Scrimba**: Control flow tutorials
- **JavaScript30**: Control flow challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Assignment dalam condition
let x = 5;
if (x = 10) {  // ❌ Seharusnya ===
    console.log("x is 10");
}

// ✅ Solusi: Gunakan === untuk comparison
if (x === 10) {
    console.log("x is 10");
}

// ❌ Infinite loop
let i = 0;
while (i < 10) {
    console.log(i);
    // Lupa increment i
}

// ✅ Solusi: Selalu increment dalam loop
while (i < 10) {
    console.log(i);
    i++;
}

// ❌ Mutasi array dalam loop
let numbers = [1, 2, 3, 4, 5];
for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] % 2 === 0) {
        numbers.splice(i, 1);  // ❌ Mengubah array saat iterasi
    }
}

// ✅ Solusi: Gunakan filter atau reverse loop
numbers = numbers.filter(num => num % 2 !== 0);
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.log untuk debugging conditions
let age = 18;
console.log("Age:", age);
console.log("Is adult:", age >= 18);

if (age >= 18) {
    console.log("Condition met: User is adult");
} else {
    console.log("Condition not met: User is minor");
}

// ✅ Debug loop dengan counter
let counter = 0;
for (let i = 0; i < 5; i++) {
    counter++;
    console.log(`Iteration ${counter}: i = ${i}`);
}

// ✅ Debug nested conditions
let user = { name: "Budi", age: 25, role: "admin" };
console.log("User:", user);

if (user.age >= 18) {
    console.log("Age check passed");
    if (user.role === "admin") {
        console.log("Role check passed");
        console.log("Full access granted");
    } else {
        console.log("Role check failed");
    }
} else {
    console.log("Age check failed");
}
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Pattern Matching (Future)
```javascript
// ✅ Switch dengan pattern matching (proposal)
function processData(data) {
    switch (data) {
        case { type: "user", name: let name }:
            return `Hello, ${name}!`;
        case { type: "admin", permissions: let perms }:
            return `Admin with ${perms.length} permissions`;
        case { type: "guest" }:
            return "Welcome, guest!";
        default:
            return "Unknown user type";
    }
}
```

### 🔄 Generator Functions
```javascript
// ✅ Generator function untuk custom iteration
function* numberGenerator(start, end) {
    for (let i = start; i <= end; i++) {
        yield i;
    }
}

for (let num of numberGenerator(1, 5)) {
    console.log(num);  // 1, 2, 3, 4, 5
}
```

### 🔄 Async Control Flow
```javascript
// ✅ Async function dengan control flow
async function processUserData(userId) {
    try {
        const user = await fetchUser(userId);
        
        if (!user) {
            throw new Error("User not found");
        }
        
        if (user.status === "inactive") {
            return { success: false, message: "User is inactive" };
        }
        
        const permissions = await fetchPermissions(userId);
        
        if (permissions.length === 0) {
            return { success: false, message: "No permissions" };
        }
        
        return { success: true, user, permissions };
        
    } catch (error) {
        console.error("Error processing user:", error);
        return { success: false, error: error.message };
    }
}
```

---

> **💡 Pro Tip**: Control flow adalah fondasi logika programming. Kuasai kondisi dan loop dengan baik untuk membuat program yang cerdas dan efisien! 