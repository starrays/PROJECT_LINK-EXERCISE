# ⚠️ Error Handling Fundamental

## 1. Apa itu Error?

**Error** adalah kondisi abnormal yang terjadi saat program berjalan, yang dapat menyebabkan program berhenti atau berperilaku tidak sesuai harapan. Bayangkan error seperti lampu peringatan di mobil - memberitahu ada sesuatu yang perlu diperbaiki.

### 🎯 Konsep Dasar
- **Error**: Kondisi abnormal dalam program
- **Exception**: Error yang dapat ditangkap dan ditangani
- **Throw**: Melempar error secara manual
- **Catch**: Menangkap dan menangani error
- **Finally**: Kode yang selalu dijalankan setelah try-catch

### 📝 Contoh Sederhana
```javascript
// Error sederhana
let result = 10 / 0;  // Infinity (tidak error, tapi hasil tidak valid)

// Error yang dapat ditangani
try {
    let user = null;
    console.log(user.name);  // TypeError: Cannot read property 'name' of null
} catch (error) {
    console.log("Error terjadi:", error.message);
}

// Error yang dilempar manual
function divide(a, b) {
    if (b === 0) {
        throw new Error("Division by zero is not allowed");
    }
    return a / b;
}
```

### 🔍 Istilah Penting
- **Error**: Kondisi abnormal dalam program
- **Exception**: Error yang dapat ditangkap
- **Throw**: Melempar error secara manual
- **Catch**: Menangkap error
- **Finally**: Kode yang selalu dijalankan
- **Stack Trace**: Informasi lokasi error dalam kode

## 2. Error Types

### 🔍 Syntax Error
```javascript
// ❌ Syntax Error - kesalahan penulisan kode
// let name = "Budi"  // Missing semicolon
// console.log(name    // Missing closing parenthesis
// if (condition {     // Missing closing brace

// ✅ Syntax yang benar
let name = "Budi";
console.log(name);
if (condition) {
    // code here
}
```

### 🔍 Runtime Error
```javascript
// ✅ Runtime Error - error saat program berjalan
let user = null;
console.log(user.name);  // TypeError: Cannot read property 'name' of null

let arr = [1, 2, 3];
console.log(arr[10]);    // undefined (tidak error, tapi tidak ada nilai)

let result = 10 / 0;     // Infinity (hasil matematika tidak valid)
```

### 🔍 Logic Error
```javascript
// ✅ Logic Error - program berjalan tapi hasil salah
function calculateAverage(numbers) {
    let sum = 0;
    for (let i = 0; i <= numbers.length; i++) {  // ❌ Seharusnya <
        sum += numbers[i];
    }
    return sum / numbers.length;  // ❌ Bisa division by zero
}

// ✅ Logic yang benar
function calculateAverage(numbers) {
    if (numbers.length === 0) {
        return 0;
    }
    
    let sum = 0;
    for (let i = 0; i < numbers.length; i++) {
        sum += numbers[i];
    }
    return sum / numbers.length;
}
```

### 🔍 Network Error
```javascript
// ✅ Network Error - error saat komunikasi dengan server
async function fetchUserData(userId) {
    try {
        const response = await fetch(`/api/users/${userId}`);
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        return await response.json();
    } catch (error) {
        console.error("Network error:", error.message);
        throw error;
    }
}
```

### 🔍 User Input Error
```javascript
// ✅ User Input Error - error karena input tidak valid
function validateEmail(email) {
    if (!email || typeof email !== 'string') {
        throw new Error("Email is required and must be a string");
    }
    
    if (!email.includes('@')) {
        throw new Error("Email must contain @ symbol");
    }
    
    if (!email.includes('.')) {
        throw new Error("Email must contain domain");
    }
    
    return true;
}

// ✅ Usage
try {
    validateEmail("invalid-email");
} catch (error) {
    console.log("Validation error:", error.message);
}
```

## 3. Try-Catch Statement

### 🔄 Basic Try-Catch
```javascript
// ✅ Basic try-catch
try {
    let user = null;
    console.log(user.name);  // Error akan terjadi
} catch (error) {
    console.log("Error terjadi:", error.message);
    console.log("Error type:", error.name);
    console.log("Stack trace:", error.stack);
}

// ✅ Try-catch dengan multiple operations
try {
    let data = JSON.parse('{"name": "Budi"}');
    console.log(data.name);
    
    let result = 10 / 0;
    console.log(result);
    
    let arr = [1, 2, 3];
    console.log(arr[10]);  // undefined, tidak error
} catch (error) {
    console.log("Error:", error.message);
}
```

### 🔄 Try-Catch dengan Finally
```javascript
// ✅ Try-catch-finally
function processFile(filename) {
    let file = null;
    
    try {
        file = openFile(filename);
        let content = readFile(file);
        return processContent(content);
    } catch (error) {
        console.log("Error processing file:", error.message);
        return null;
    } finally {
        if (file) {
            closeFile(file);  // Selalu dijalankan
        }
    }
}

// ✅ Finally dengan return
function getData() {
    try {
        return "Data retrieved successfully";
    } catch (error) {
        return "Error occurred";
    } finally {
        console.log("Cleanup always happens");
    }
}

let result = getData();
console.log(result);  // "Data retrieved successfully"
console.log("Cleanup always happens");  // Selalu dijalankan
```

### 🔄 Nested Try-Catch
```javascript
// ✅ Nested try-catch
function processUserData(userId) {
    try {
        let user = fetchUser(userId);
        
        try {
            let userData = JSON.parse(user);
            return processUser(userData);
        } catch (parseError) {
            console.log("Error parsing user data:", parseError.message);
            return null;
        }
        
    } catch (fetchError) {
        console.log("Error fetching user:", fetchError.message);
        return null;
    }
}

// ✅ Try-catch dalam loop
let users = ["user1", "user2", "user3", null, "user5"];

for (let user of users) {
    try {
        if (!user) {
            throw new Error("User is null");
        }
        console.log(`Processing ${user}`);
    } catch (error) {
        console.log(`Skipping user due to error: ${error.message}`);
        continue;  // Lanjut ke user berikutnya
    }
}
```

### 🔄 Error Propagation
```javascript
// ✅ Error propagation - error naik ke level atas
function level3() {
    throw new Error("Error from level 3");
}

function level2() {
    try {
        level3();
    } catch (error) {
        console.log("Level 2 caught error:", error.message);
        throw error;  // Re-throw error
    }
}

function level1() {
    try {
        level2();
    } catch (error) {
        console.log("Level 1 caught error:", error.message);
        // Error tidak di-re-throw, jadi berhenti di sini
    }
}

level1();
```

## 4. Error Object

### 🔍 Error Properties
```javascript
// ✅ Error object properties
try {
    let user = null;
    console.log(user.name);
} catch (error) {
    console.log("Error name:", error.name);        // "TypeError"
    console.log("Error message:", error.message);  // "Cannot read property 'name' of null"
    console.log("Error stack:", error.stack);      // Stack trace
    console.log("Error constructor:", error.constructor.name); // "TypeError"
}

// ✅ Custom error dengan properties
class ValidationError extends Error {
    constructor(message, field) {
        super(message);
        this.name = "ValidationError";
        this.field = field;
        this.timestamp = new Date();
    }
}

try {
    throw new ValidationError("Email is invalid", "email");
} catch (error) {
    console.log("Error:", error.message);
    console.log("Field:", error.field);
    console.log("Timestamp:", error.timestamp);
}
```

### 🔍 Custom Error Messages
```javascript
// ✅ Custom error messages
function divide(a, b) {
    if (typeof a !== 'number' || typeof b !== 'number') {
        throw new Error("Both arguments must be numbers");
    }
    
    if (b === 0) {
        throw new Error("Division by zero is not allowed");
    }
    
    return a / b;
}

// ✅ Error dengan context
function processUser(user) {
    if (!user) {
        throw new Error("User object is required");
    }
    
    if (!user.name) {
        throw new Error("User name is required");
    }
    
    if (!user.email) {
        throw new Error("User email is required");
    }
    
    return `Processing user: ${user.name} (${user.email})`;
}

// ✅ Usage dengan error handling
try {
    let result = divide(10, 0);
} catch (error) {
    console.log("Calculation error:", error.message);
}

try {
    let result = processUser({ name: "Budi" }); // Missing email
} catch (error) {
    console.log("User processing error:", error.message);
}
```

### 🔍 Error Inheritance
```javascript
// ✅ Custom error classes
class NetworkError extends Error {
    constructor(message, statusCode) {
        super(message);
        this.name = "NetworkError";
        this.statusCode = statusCode;
    }
}

class ValidationError extends Error {
    constructor(message, field) {
        super(message);
        this.name = "ValidationError";
        this.field = field;
    }
}

class DatabaseError extends Error {
    constructor(message, query) {
        super(message);
        this.name = "DatabaseError";
        this.query = query;
    }
}

// ✅ Error handling dengan type checking
function handleError(error) {
    if (error instanceof NetworkError) {
        console.log(`Network error (${error.statusCode}): ${error.message}`);
    } else if (error instanceof ValidationError) {
        console.log(`Validation error in field '${error.field}': ${error.message}`);
    } else if (error instanceof DatabaseError) {
        console.log(`Database error in query '${error.query}': ${error.message}`);
    } else {
        console.log(`Unknown error: ${error.message}`);
    }
}

// ✅ Usage
try {
    throw new NetworkError("Connection failed", 500);
} catch (error) {
    handleError(error);
}
```

### 🔍 Error Bubbling
```javascript
// ✅ Error bubbling - error naik ke level atas
function level3() {
    throw new Error("Original error");
}

function level2() {
    try {
        level3();
    } catch (error) {
        // Menambah context ke error
        error.message = `Level 2: ${error.message}`;
        throw error;
    }
}

function level1() {
    try {
        level2();
    } catch (error) {
        error.message = `Level 1: ${error.message}`;
        throw error;
    }
}

try {
    level1();
} catch (error) {
    console.log("Final error:", error.message);
    // Output: "Final error: Level 1: Level 2: Original error"
}
```

## 5. Debugging Techniques

### 🔍 Console.log Debugging
```javascript
// ✅ Console.log untuk debugging
function processData(data) {
    console.log("Input data:", data);
    
    if (!data) {
        console.log("Data is null or undefined");
        return null;
    }
    
    console.log("Data type:", typeof data);
    console.log("Data length:", data.length);
    
    let result = data.map(item => {
        console.log("Processing item:", item);
        return item * 2;
    });
    
    console.log("Final result:", result);
    return result;
}

// ✅ Debug dengan labels
function calculateTotal(items) {
    console.log("=== CALCULATE TOTAL ===");
    console.log("Items:", items);
    
    let total = 0;
    for (let i = 0; i < items.length; i++) {
        console.log(`Item ${i}:`, items[i]);
        total += items[i];
        console.log(`Running total: ${total}`);
    }
    
    console.log("Final total:", total);
    return total;
}
```

### 🔍 Browser Developer Tools
```javascript
// ✅ Debugger statement
function complexFunction(data) {
    debugger;  // Browser akan pause di sini
    
    let result = data.map(item => {
        if (item > 10) {
            debugger;  // Pause jika item > 10
        }
        return item * 2;
    });
    
    return result;
}

// ✅ Console methods
function debugObject(obj) {
    console.log("Object:", obj);
    console.table(obj);  // Untuk array of objects
    console.dir(obj);    // Detailed object view
    console.trace();     // Stack trace
}

// ✅ Performance debugging
function performanceTest() {
    console.time("Processing time");
    
    // Some expensive operation
    for (let i = 0; i < 1000000; i++) {
        Math.random();
    }
    
    console.timeEnd("Processing time");
}
```

### 🔍 Breakpoints
```javascript
// ✅ Conditional breakpoints (dalam browser dev tools)
function processUsers(users) {
    for (let user of users) {
        // Set breakpoint dengan condition: user.age < 18
        if (user.age < 18) {
            console.log("Minor user found:", user);
        }
        
        // Set breakpoint dengan condition: user.name === "Budi"
        if (user.name === "Budi") {
            console.log("Budi found:", user);
        }
    }
}

// ✅ Logging levels
const DEBUG = {
    log: (message) => console.log(`[DEBUG] ${message}`),
    warn: (message) => console.warn(`[DEBUG] ${message}`),
    error: (message) => console.error(`[DEBUG] ${message}`)
};

function debugFunction() {
    DEBUG.log("Function started");
    
    try {
        // Some operation
        DEBUG.log("Operation completed");
    } catch (error) {
        DEBUG.error("Operation failed: " + error.message);
    }
}
```

### 🔍 Step-through Debugging
```javascript
// ✅ Step-by-step debugging
function calculateTax(income) {
    let tax = 0;
    
    if (income <= 50000000) {
        tax = income * 0.05;
    } else if (income <= 250000000) {
        tax = 2500000 + (income - 50000000) * 0.15;
    } else if (income <= 500000000) {
        tax = 32500000 + (income - 250000000) * 0.25;
    } else {
        tax = 95000000 + (income - 500000000) * 0.30;
    }
    
    return tax;
}

// ✅ Debug dengan step-through
function debugTaxCalculation(income) {
    console.log("Income:", income);
    
    let tax = 0;
    console.log("Initial tax:", tax);
    
    if (income <= 50000000) {
        tax = income * 0.05;
        console.log("Tax bracket: 5%");
    } else if (income <= 250000000) {
        tax = 2500000 + (income - 50000000) * 0.15;
        console.log("Tax bracket: 15%");
    } else if (income <= 500000000) {
        tax = 32500000 + (income - 250000000) * 0.25;
        console.log("Tax bracket: 25%");
    } else {
        tax = 95000000 + (income - 500000000) * 0.30;
        console.log("Tax bracket: 30%");
    }
    
    console.log("Final tax:", tax);
    return tax;
}
```

## 6. Best Practices

### 🛡️ Defensive Programming
```javascript
// ✅ Input validation
function processUser(user) {
    // Validate input
    if (!user) {
        throw new Error("User object is required");
    }
    
    if (typeof user !== 'object') {
        throw new Error("User must be an object");
    }
    
    if (!user.name || typeof user.name !== 'string') {
        throw new Error("User must have a valid name");
    }
    
    if (!user.age || typeof user.age !== 'number' || user.age < 0) {
        throw new Error("User must have a valid age");
    }
    
    // Process user
    return {
        name: user.name.toUpperCase(),
        age: user.age,
        isAdult: user.age >= 18
    };
}

// ✅ Safe property access
function getUserName(user) {
    return user && user.name || "Anonymous";
}

function getNestedValue(obj, path) {
    return path.split('.').reduce((current, key) => {
        return current && current[key] !== undefined ? current[key] : null;
    }, obj);
}

// ✅ Default values
function createConfig(options = {}) {
    return {
        port: options.port || 3000,
        host: options.host || "localhost",
        debug: options.debug || false,
        timeout: options.timeout || 5000
    };
}
```

### 🔒 Graceful Degradation
```javascript
// ✅ Graceful degradation - program tetap berjalan meski ada error
function loadUserProfile(userId) {
    try {
        const user = fetchUserFromAPI(userId);
        return user;
    } catch (error) {
        console.warn("Failed to load user profile:", error.message);
        
        // Fallback ke data default
        return {
            id: userId,
            name: "Unknown User",
            avatar: "/default-avatar.png",
            isDefault: true
        };
    }
}

// ✅ Feature detection
function useAdvancedFeature() {
    try {
        // Check if feature is available
        if (typeof window.advancedFeature === 'undefined') {
            throw new Error("Advanced feature not available");
        }
        
        return window.advancedFeature.doSomething();
    } catch (error) {
        console.warn("Advanced feature not available, using fallback");
        return fallbackImplementation();
    }
}
```

### 📊 User-friendly Error Messages
```javascript
// ✅ User-friendly error messages
function validateEmail(email) {
    try {
        if (!email) {
            throw new Error("Email address is required");
        }
        
        if (typeof email !== 'string') {
            throw new Error("Email must be a text");
        }
        
        if (!email.includes('@')) {
            throw new Error("Email must contain @ symbol");
        }
        
        if (!email.includes('.')) {
            throw new Error("Email must contain a domain (e.g., .com)");
        }
        
        if (email.length < 5) {
            throw new Error("Email is too short");
        }
        
        return true;
    } catch (error) {
        // Convert technical error to user-friendly message
        const userMessages = {
            "Email address is required": "Please enter your email address",
            "Email must be a text": "Email must be text only",
            "Email must contain @ symbol": "Please include @ in your email address",
            "Email must contain a domain (e.g., .com)": "Please include a domain (e.g., .com, .org)",
            "Email is too short": "Email address is too short"
        };
        
        throw new Error(userMessages[error.message] || "Please enter a valid email address");
    }
}

// ✅ Error categorization
function categorizeError(error) {
    if (error.message.includes("network") || error.message.includes("fetch")) {
        return {
            type: "NETWORK_ERROR",
            userMessage: "Please check your internet connection and try again",
            technicalMessage: error.message
        };
    }
    
    if (error.message.includes("validation")) {
        return {
            type: "VALIDATION_ERROR",
            userMessage: "Please check your input and try again",
            technicalMessage: error.message
        };
    }
    
    if (error.message.includes("permission") || error.message.includes("access")) {
        return {
            type: "PERMISSION_ERROR",
            userMessage: "You don't have permission to perform this action",
            technicalMessage: error.message
        };
    }
    
    return {
        type: "UNKNOWN_ERROR",
        userMessage: "Something went wrong. Please try again later.",
        technicalMessage: error.message
    };
}
```

## 7. Common Error Patterns

### 🚫 Undefined Variables
```javascript
// ❌ Undefined variable error
function processData() {
    console.log(data);  // ReferenceError: data is not defined
}

// ✅ Solusi: Selalu deklarasikan variabel
function processData() {
    let data = fetchData();
    console.log(data);
}

// ✅ Solusi: Gunakan default values
function processData(data = []) {
    console.log(data);
}
```

### 🚫 Null Reference Errors
```javascript
// ❌ Null reference error
let user = null;
console.log(user.name);  // TypeError: Cannot read property 'name' of null

// ✅ Solusi: Null checking
let user = null;
if (user) {
    console.log(user.name);
} else {
    console.log("User not found");
}

// ✅ Solusi: Optional chaining (ES2020)
let user = null;
console.log(user?.name);  // undefined (tidak error)

// ✅ Solusi: Default values
let user = null;
console.log(user?.name || "Anonymous");
```

### 🚫 Type Errors
```javascript
// ❌ Type error
function addNumbers(a, b) {
    return a + b;
}

console.log(addNumbers("5", 3));  // "53" (concatenation, bukan addition)

// ✅ Solusi: Type checking
function addNumbers(a, b) {
    if (typeof a !== 'number' || typeof b !== 'number') {
        throw new Error("Both arguments must be numbers");
    }
    return a + b;
}

// ✅ Solusi: Type conversion
function addNumbers(a, b) {
    const numA = Number(a);
    const numB = Number(b);
    
    if (isNaN(numA) || isNaN(numB)) {
        throw new Error("Arguments must be valid numbers");
    }
    
    return numA + numB;
}
```

### 🚫 Network Timeout Errors
```javascript
// ❌ Network timeout
async function fetchData() {
    const response = await fetch('/api/data');
    return response.json();
}

// ✅ Solusi: Timeout handling
async function fetchData(timeout = 5000) {
    const controller = new AbortController();
    const timeoutId = setTimeout(() => controller.abort(), timeout);
    
    try {
        const response = await fetch('/api/data', {
            signal: controller.signal
        });
        
        clearTimeout(timeoutId);
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        return await response.json();
    } catch (error) {
        clearTimeout(timeoutId);
        
        if (error.name === 'AbortError') {
            throw new Error('Request timed out');
        }
        
        throw error;
    }
}
```

## 8. Studi Kasus Praktis

### 🛒 E-commerce Error Handling
```javascript
// ✅ E-commerce error handling system
class OrderProcessor {
    constructor() {
        this.errors = [];
    }
    
    processOrder(order) {
        try {
            // Validate order
            this.validateOrder(order);
            
            // Process payment
            const paymentResult = this.processPayment(order.payment);
            
            // Update inventory
            this.updateInventory(order.items);
            
            // Send confirmation
            this.sendConfirmation(order.customer.email);
            
            return { success: true, orderId: this.generateOrderId() };
            
        } catch (error) {
            this.errors.push({
                timestamp: new Date(),
                error: error.message,
                orderId: order.id
            });
            
            // Rollback changes if needed
            this.rollbackChanges(order);
            
            return { success: false, error: error.message };
        }
    }
    
    validateOrder(order) {
        if (!order) {
            throw new Error("Order is required");
        }
        
        if (!order.customer || !order.customer.email) {
            throw new Error("Valid customer information is required");
        }
        
        if (!order.items || order.items.length === 0) {
            throw new Error("Order must contain at least one item");
        }
        
        if (!order.payment || !order.payment.method) {
            throw new Error("Valid payment information is required");
        }
        
        // Validate each item
        for (let item of order.items) {
            if (!item.productId || !item.quantity || item.quantity <= 0) {
                throw new Error("Each item must have valid product ID and quantity");
            }
        }
    }
    
    processPayment(payment) {
        try {
            // Simulate payment processing
            if (payment.method === "credit_card") {
                if (!payment.cardNumber || payment.cardNumber.length < 13) {
                    throw new Error("Invalid credit card number");
                }
            } else if (payment.method === "bank_transfer") {
                if (!payment.accountNumber) {
                    throw new Error("Bank account number is required");
                }
            } else {
                throw new Error("Unsupported payment method");
            }
            
            return { success: true, transactionId: "TXN" + Date.now() };
            
        } catch (error) {
            throw new Error(`Payment processing failed: ${error.message}`);
        }
    }
    
    updateInventory(items) {
        try {
            for (let item of items) {
                // Simulate inventory update
                if (Math.random() < 0.1) { // 10% chance of failure
                    throw new Error(`Insufficient stock for product ${item.productId}`);
                }
            }
        } catch (error) {
            throw new Error(`Inventory update failed: ${error.message}`);
        }
    }
    
    sendConfirmation(email) {
        try {
            // Simulate email sending
            if (!email || !email.includes('@')) {
                throw new Error("Invalid email address");
            }
            
            console.log(`Confirmation email sent to ${email}`);
            
        } catch (error) {
            // Don't throw error for email failure, just log it
            console.warn(`Failed to send confirmation email: ${error.message}`);
        }
    }
    
    rollbackChanges(order) {
        // Simulate rollback
        console.log("Rolling back changes for order:", order.id);
    }
    
    generateOrderId() {
        return "ORD" + Date.now();
    }
    
    getErrors() {
        return this.errors;
    }
}

// ✅ Usage
const processor = new OrderProcessor();

const order = {
    id: "12345",
    customer: { email: "budi@email.com" },
    items: [
        { productId: "P001", quantity: 2 },
        { productId: "P002", quantity: 1 }
    ],
    payment: {
        method: "credit_card",
        cardNumber: "1234567890123456"
    }
};

const result = processor.processOrder(order);
console.log(result);
```

### 🎮 Game Error Handling
```javascript
// ✅ Game error handling system
class GameEngine {
    constructor() {
        this.state = {
            player: { health: 100, level: 1, experience: 0 },
            enemies: [],
            gameOver: false
        };
        this.errors = [];
    }
    
    updatePlayerHealth(damage) {
        try {
            if (this.state.gameOver) {
                throw new Error("Game is already over");
            }
            
            if (typeof damage !== 'number' || damage < 0) {
                throw new Error("Damage must be a positive number");
            }
            
            this.state.player.health = Math.max(0, this.state.player.health - damage);
            
            if (this.state.player.health === 0) {
                this.state.gameOver = true;
                return { alive: false, message: "Game Over!" };
            }
            
            return { alive: true, health: this.state.player.health };
            
        } catch (error) {
            this.logError("updatePlayerHealth", error);
            return { alive: false, error: error.message };
        }
    }
    
    addExperience(exp) {
        try {
            if (this.state.gameOver) {
                throw new Error("Cannot gain experience when game is over");
            }
            
            if (typeof exp !== 'number' || exp < 0) {
                throw new Error("Experience must be a positive number");
            }
            
            this.state.player.experience += exp;
            
            // Level up logic
            const requiredExp = this.state.player.level * 100;
            if (this.state.player.experience >= requiredExp) {
                this.levelUp();
            }
            
            return {
                level: this.state.player.level,
                experience: this.state.player.experience
            };
            
        } catch (error) {
            this.logError("addExperience", error);
            return { error: error.message };
        }
    }
    
    levelUp() {
        try {
            this.state.player.level++;
            this.state.player.experience -= (this.state.player.level - 1) * 100;
            this.state.player.health = Math.min(100, this.state.player.health + 20);
            
            console.log(`Level up! You are now level ${this.state.player.level}`);
            
        } catch (error) {
            this.logError("levelUp", error);
        }
    }
    
    spawnEnemy() {
        try {
            if (this.state.gameOver) {
                throw new Error("Cannot spawn enemies when game is over");
            }
            
            const enemy = {
                id: Date.now(),
                health: 50,
                level: Math.floor(Math.random() * 3) + 1
            };
            
            this.state.enemies.push(enemy);
            return { success: true, enemy };
            
        } catch (error) {
            this.logError("spawnEnemy", error);
            return { success: false, error: error.message };
        }
    }
    
    attackEnemy(enemyId, damage) {
        try {
            if (this.state.gameOver) {
                throw new Error("Cannot attack when game is over");
            }
            
            const enemy = this.state.enemies.find(e => e.id === enemyId);
            if (!enemy) {
                throw new Error("Enemy not found");
            }
            
            if (typeof damage !== 'number' || damage < 0) {
                throw new Error("Damage must be a positive number");
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
            
            return {
                success: true,
                enemyDefeated: false,
                enemyHealth: enemy.health
            };
            
        } catch (error) {
            this.logError("attackEnemy", error);
            return { success: false, error: error.message };
        }
    }
    
    logError(method, error) {
        this.errors.push({
            timestamp: new Date(),
            method: method,
            error: error.message,
            stack: error.stack
        });
        
        console.error(`Game error in ${method}:`, error.message);
    }
    
    getErrors() {
        return this.errors;
    }
    
    getGameState() {
        return { ...this.state };
    }
}

// ✅ Usage
const game = new GameEngine();

// Test various scenarios
console.log(game.updatePlayerHealth(20));  // Normal damage
console.log(game.addExperience(50));       // Normal experience
console.log(game.spawnEnemy());           // Spawn enemy
console.log(game.attackEnemy(123, 25));   // Attack enemy

// Test error scenarios
console.log(game.updatePlayerHealth(-5));  // Invalid damage
console.log(game.addExperience("invalid")); // Invalid experience
console.log(game.attackEnemy(999, 25));   // Non-existent enemy
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Error Handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- **JavaScript.info**: [Error Handling](https://javascript.info/try-catch)
- **W3Schools**: [JavaScript Errors](https://www.w3schools.com/js/js_errors.asp)

### 📖 Buku Rekomendasi
- "Eloquent JavaScript" by Marijn Haverbeke
- "JavaScript: The Definitive Guide" by David Flanagan
- "You Don't Know JS: Types & Grammar" by Kyle Simpson

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Error Handling Tutorial
- **The Net Ninja**: JavaScript Try-Catch & Error Handling
- **Programming with Mosh**: JavaScript Error Handling

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen error handling
- **JSFiddle**: Untuk testing try-catch
- **Replit**: Untuk project error handling
- **Browser DevTools**: Untuk debugging errors

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan try-catch dasar
2. **Learn Error Types**: Kuasai berbagai jenis error
3. **Practice Debugging**: Latihan debugging techniques
4. **Build Projects**: Aplikasikan dalam project nyata
5. **Master Best Practices**: Pelajari defensive programming

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep error handling
2. **Practice** → Tulis kode dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki
5. **Repeat** → Ulangi dengan konsep error handling baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Error Handling
- **freeCodeCamp**: JavaScript Error Handling
- **Scrimba**: Error handling tutorials
- **JavaScript30**: Error handling challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Tidak menangani error
function processData(data) {
    return data.map(item => item * 2);  // Error jika data null
}

// ✅ Solusi: Selalu handle error
function processData(data) {
    try {
        if (!Array.isArray(data)) {
            throw new Error("Data must be an array");
        }
        return data.map(item => item * 2);
    } catch (error) {
        console.error("Error processing data:", error.message);
        return [];
    }
}

// ❌ Error dalam async function
async function fetchData() {
    const response = await fetch('/api/data');
    return response.json();  // Error jika response tidak ok
}

// ✅ Solusi: Handle async errors
async function fetchData() {
    try {
        const response = await fetch('/api/data');
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        return await response.json();
    } catch (error) {
        console.error("Failed to fetch data:", error.message);
        throw error;
    }
}
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.error untuk error logging
try {
    // Some operation
} catch (error) {
    console.error("Error occurred:", error.message);
    console.error("Stack trace:", error.stack);
}

// ✅ Gunakan error boundaries (untuk React)
class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }
    
    static getDerivedStateFromError(error) {
        return { hasError: true };
    }
    
    componentDidCatch(error, errorInfo) {
        console.error("Error caught by boundary:", error, errorInfo);
    }
    
    render() {
        if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
        }
        
        return this.props.children;
    }
}

// ✅ Gunakan error monitoring tools
function logError(error, context = {}) {
    // Send to error monitoring service
    console.error("Error logged:", {
        message: error.message,
        stack: error.stack,
        timestamp: new Date(),
        context: context
    });
}
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Error Boundaries (React)
```javascript
// ✅ Error boundary untuk React components
class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false, error: null };
    }
    
    static getDerivedStateFromError(error) {
        return { hasError: true, error };
    }
    
    componentDidCatch(error, errorInfo) {
        console.error("Error caught:", error, errorInfo);
        // Send to error reporting service
    }
    
    render() {
        if (this.state.hasError) {
            return (
                <div className="error-boundary">
                    <h2>Something went wrong</h2>
                    <button onClick={() => this.setState({ hasError: false })}>
                        Try again
                    </button>
                </div>
            );
        }
        
        return this.props.children;
    }
}
```

### 🔄 Global Error Handling
```javascript
// ✅ Global error handler
window.addEventListener('error', function(event) {
    console.error('Global error:', event.error);
    // Send to error reporting service
});

// ✅ Unhandled promise rejection handler
window.addEventListener('unhandledrejection', function(event) {
    console.error('Unhandled promise rejection:', event.reason);
    // Send to error reporting service
});

// ✅ Custom error handler
function setupGlobalErrorHandling() {
    const originalError = console.error;
    
    console.error = function(...args) {
        // Log to external service
        logToExternalService(args);
        
        // Call original console.error
        originalError.apply(console, args);
    };
}
```

---

> **💡 Pro Tip**: Error handling yang baik membuat aplikasi lebih robust dan user-friendly. Selalu handle error dengan graceful dan informatif! 