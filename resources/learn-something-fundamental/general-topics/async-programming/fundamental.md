# ⏱️ Async Programming Fundamental

## 1. Apa itu Async Programming?

**Async Programming** adalah cara menangani operasi yang membutuhkan waktu tanpa menghentikan eksekusi program. Bayangkan seperti restoran - pelayan tidak perlu menunggu masak selesai untuk melayani pelanggan lain.

### 🎯 Konsep Dasar
- **Synchronous**: Operasi berjalan satu per satu (blocking)
- **Asynchronous**: Operasi berjalan bersamaan (non-blocking)
- **Callback**: Function yang dipanggil setelah operasi selesai
- **Promise**: Object yang merepresentasikan operasi async
- **Async/Await**: Syntax modern untuk menangani async operations

### 📝 Contoh Sederhana
```javascript
// Synchronous (blocking)
console.log("Start");
let result = heavyCalculation();  // Program berhenti di sini
console.log("End");

// Asynchronous (non-blocking)
console.log("Start");
setTimeout(() => {
    console.log("Async operation completed");
}, 1000);
console.log("End");  // Ini dijalankan sebelum async selesai
```

### 🔍 Istilah Penting
- **Synchronous**: Operasi yang berjalan secara berurutan
- **Asynchronous**: Operasi yang berjalan bersamaan
- **Callback**: Function yang dipanggil setelah operasi selesai
- **Promise**: Object untuk menangani async operations
- **Event Loop**: Mekanisme JavaScript untuk menangani async
- **Microtask**: Task dengan prioritas tinggi dalam event loop

## 2. Callbacks

### 🔄 Callback Function Concept
```javascript
// ✅ Basic callback function
function greetUser(name, callback) {
    console.log(`Hello, ${name}!`);
    callback();
}

greetUser("Budi", function() {
    console.log("Greeting completed!");
});

// ✅ Callback dengan parameter
function processData(data, callback) {
    console.log("Processing data:", data);
    let result = data * 2;
    callback(result);
}

processData(5, function(result) {
    console.log("Result:", result);
});

// ✅ Callback dengan error handling
function divideNumbers(a, b, callback) {
    if (b === 0) {
        callback(new Error("Division by zero"), null);
    } else {
        callback(null, a / b);
    }
}

divideNumbers(10, 2, function(error, result) {
    if (error) {
        console.error("Error:", error.message);
    } else {
        console.log("Result:", result);
    }
});
```

### 🔄 Passing Functions as Arguments
```javascript
// ✅ Function sebagai callback
function add(a, b) {
    return a + b;
}

function multiply(a, b) {
    return a * b;
}

function calculate(a, b, operation) {
    return operation(a, b);
}

console.log(calculate(5, 3, add));      // 8
console.log(calculate(5, 3, multiply)); // 15

// ✅ Anonymous function sebagai callback
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(num) {
    console.log(num * 2);
});

// ✅ Arrow function sebagai callback
numbers.forEach(num => console.log(num * 2));

// ✅ Callback dengan multiple parameters
function processUser(user, onSuccess, onError) {
    if (user && user.name) {
        onSuccess(`Hello, ${user.name}!`);
    } else {
        onError("Invalid user data");
    }
}

processUser(
    { name: "Budi" },
    function(message) {
        console.log("Success:", message);
    },
    function(error) {
        console.error("Error:", error);
    }
);
```

### 🔄 Callback Hell Problem
```javascript
// ❌ Callback hell - nested callbacks yang sulit dibaca
function processUserData(userId, callback) {
    fetchUser(userId, function(user) {
        if (user) {
            fetchUserProfile(user.id, function(profile) {
                if (profile) {
                    fetchUserPosts(user.id, function(posts) {
                        if (posts) {
                            callback(null, { user, profile, posts });
                        } else {
                            callback(new Error("Failed to fetch posts"));
                        }
                    });
                } else {
                    callback(new Error("Failed to fetch profile"));
                }
            });
        } else {
            callback(new Error("Failed to fetch user"));
        }
    });
}

// ✅ Solusi dengan Promise
function processUserData(userId) {
    return fetchUser(userId)
        .then(user => {
            return Promise.all([
                Promise.resolve(user),
                fetchUserProfile(user.id),
                fetchUserPosts(user.id)
            ]);
        })
        .then(([user, profile, posts]) => {
            return { user, profile, posts };
        });
}
```

### 🔄 Error Handling dengan Callbacks
```javascript
// ✅ Error-first callback pattern
function readFile(filename, callback) {
    // Simulate file reading
    setTimeout(() => {
        if (filename === "error.txt") {
            callback(new Error("File not found"), null);
        } else {
            callback(null, `Content of ${filename}`);
        }
    }, 1000);
}

// ✅ Usage dengan error handling
readFile("data.txt", function(error, data) {
    if (error) {
        console.error("Error reading file:", error.message);
    } else {
        console.log("File content:", data);
    }
});

// ✅ Multiple async operations dengan error handling
function processMultipleFiles(filenames, callback) {
    let results = [];
    let errors = [];
    let completed = 0;
    
    filenames.forEach((filename, index) => {
        readFile(filename, function(error, data) {
            if (error) {
                errors.push({ filename, error: error.message });
            } else {
                results.push({ filename, data });
            }
            
            completed++;
            
            if (completed === filenames.length) {
                callback(errors.length > 0 ? errors : null, results);
            }
        });
    });
}
```

## 3. Promises

### 🔄 Promise States
```javascript
// ✅ Promise states: pending, fulfilled, rejected
let promise = new Promise((resolve, reject) => {
    // Promise is in pending state
    setTimeout(() => {
        resolve("Success!");  // Promise becomes fulfilled
        // OR
        // reject("Error!");  // Promise becomes rejected
    }, 1000);
});

// ✅ Promise constructor
function createPromise(shouldResolve = true) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (shouldResolve) {
                resolve("Operation completed successfully");
            } else {
                reject(new Error("Operation failed"));
            }
        }, 1000);
    });
}

// ✅ Using promises
createPromise(true)
    .then(result => console.log("Success:", result))
    .catch(error => console.error("Error:", error.message));

createPromise(false)
    .then(result => console.log("Success:", result))
    .catch(error => console.error("Error:", error.message));
```

### 🔄 Promise Constructor
```javascript
// ✅ Basic promise constructor
function fetchData() {
    return new Promise((resolve, reject) => {
        // Simulate API call
        setTimeout(() => {
            const data = { id: 1, name: "Budi", age: 25 };
            
            if (Math.random() > 0.5) {
                resolve(data);
            } else {
                reject(new Error("Failed to fetch data"));
            }
        }, 1000);
    });
}

// ✅ Promise dengan timeout
function fetchWithTimeout(url, timeout = 5000) {
    return new Promise((resolve, reject) => {
        const timeoutId = setTimeout(() => {
            reject(new Error("Request timed out"));
        }, timeout);
        
        // Simulate fetch
        setTimeout(() => {
            clearTimeout(timeoutId);
            resolve({ data: "Response data" });
        }, Math.random() * 3000);
    });
}

// ✅ Promise untuk file operations
function readFileAsync(filename) {
    return new Promise((resolve, reject) => {
        // Simulate file reading
        setTimeout(() => {
            if (filename === "error.txt") {
                reject(new Error("File not found"));
            } else {
                resolve(`Content of ${filename}`);
            }
        }, 500);
    });
}
```

### 🔄 .then() dan .catch()
```javascript
// ✅ Basic .then() dan .catch()
fetchData()
    .then(data => {
        console.log("Data received:", data);
        return data.name;  // Pass to next .then()
    })
    .then(name => {
        console.log("User name:", name);
    })
    .catch(error => {
        console.error("Error:", error.message);
    });

// ✅ Promise chaining
function processUser(userId) {
    return fetchUser(userId)
        .then(user => {
            console.log("User fetched:", user);
            return fetchUserProfile(user.id);
        })
        .then(profile => {
            console.log("Profile fetched:", profile);
            return fetchUserPosts(user.id);
        })
        .then(posts => {
            console.log("Posts fetched:", posts);
            return { user, profile, posts };
        })
        .catch(error => {
            console.error("Error in processUser:", error.message);
            throw error;  // Re-throw untuk handling di level atas
        });
}

// ✅ Error handling dalam chain
function safeOperation() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (Math.random() > 0.5) {
                resolve("Success");
            } else {
                reject(new Error("Random failure"));
            }
        }, 1000);
    });
}

safeOperation()
    .then(result => {
        console.log("First operation:", result);
        return safeOperation();  // Chain another operation
    })
    .then(result => {
        console.log("Second operation:", result);
    })
    .catch(error => {
        console.error("Any operation failed:", error.message);
    });
```

### 🔄 Promise Chaining
```javascript
// ✅ Promise chaining dengan data transformation
function getUserData(userId) {
    return fetchUser(userId)
        .then(user => {
            console.log("User:", user);
            return user.id;
        })
        .then(userId => {
            return fetchUserProfile(userId);
        })
        .then(profile => {
            console.log("Profile:", profile);
            return profile.email;
        })
        .then(email => {
            return sendEmail(email, "Welcome!");
        })
        .then(result => {
            console.log("Email sent:", result);
            return "All operations completed";
        });
}

// ✅ Promise chaining dengan error recovery
function resilientOperation() {
    return fetchData()
        .then(data => {
            console.log("Primary data source:", data);
            return data;
        })
        .catch(error => {
            console.log("Primary source failed, trying backup:", error.message);
            return fetchBackupData();  // Fallback
        })
        .then(data => {
            console.log("Final data:", data);
            return data;
        });
}
```

### 🔄 Promise.all() dan Promise.race()
```javascript
// ✅ Promise.all() - menunggu semua promise selesai
function fetchMultipleUsers(userIds) {
    const promises = userIds.map(id => fetchUser(id));
    
    return Promise.all(promises)
        .then(users => {
            console.log("All users fetched:", users);
            return users;
        })
        .catch(error => {
            console.error("One or more users failed to fetch:", error.message);
            throw error;
        });
}

// ✅ Promise.all() dengan timeout
function fetchWithTimeout(promises, timeout = 5000) {
    const timeoutPromise = new Promise((_, reject) => {
        setTimeout(() => reject(new Error("Timeout")), timeout);
    });
    
    return Promise.all([...promises, timeoutPromise])
        .then(results => {
            results.pop(); // Remove timeout result
            return results;
        });
}

// ✅ Promise.race() - menunggu promise pertama selesai
function fetchFromMultipleSources(urls) {
    const promises = urls.map(url => fetch(url));
    
    return Promise.race(promises)
        .then(response => {
            console.log("Fastest response:", response);
            return response;
        })
        .catch(error => {
            console.error("All sources failed:", error.message);
            throw error;
        });
}

// ✅ Promise.race() untuk timeout
function fetchWithTimeout(url, timeout = 5000) {
    const fetchPromise = fetch(url);
    const timeoutPromise = new Promise((_, reject) => {
        setTimeout(() => reject(new Error("Request timed out")), timeout);
    });
    
    return Promise.race([fetchPromise, timeoutPromise]);
}
```

## 4. Async/Await

### 🔄 Async Function Declaration
```javascript
// ✅ Basic async function
async function fetchUserData(userId) {
    try {
        const user = await fetchUser(userId);
        console.log("User:", user);
        return user;
    } catch (error) {
        console.error("Error fetching user:", error.message);
        throw error;
    }
}

// ✅ Async function dengan return
async function calculateTotal(items) {
    let total = 0;
    
    for (let item of items) {
        const price = await fetchItemPrice(item.id);
        total += price * item.quantity;
    }
    
    return total;
}

// ✅ Async arrow function
const processData = async (data) => {
    const processed = await processAsync(data);
    return processed;
};

// ✅ Async function dalam object
const apiClient = {
    async fetchUser(id) {
        const response = await fetch(`/api/users/${id}`);
        return response.json();
    },
    
    async createUser(userData) {
        const response = await fetch('/api/users', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(userData)
        });
        return response.json();
    }
};
```

### 🔄 Await Keyword
```javascript
// ✅ Basic await usage
async function processUser(userId) {
    const user = await fetchUser(userId);
    const profile = await fetchUserProfile(user.id);
    const posts = await fetchUserPosts(user.id);
    
    return { user, profile, posts };
}

// ✅ Await dengan error handling
async function safeOperation() {
    try {
        const result = await riskyOperation();
        return result;
    } catch (error) {
        console.error("Operation failed:", error.message);
        return null;
    }
}

// ✅ Await dalam loops
async function processItems(items) {
    const results = [];
    
    // Sequential processing
    for (let item of items) {
        const result = await processItem(item);
        results.push(result);
    }
    
    return results;
}

// ✅ Parallel processing dengan Promise.all()
async function processItemsParallel(items) {
    const promises = items.map(item => processItem(item));
    return await Promise.all(promises);
}
```

### 🔄 Error Handling dengan Try-Catch
```javascript
// ✅ Async/await dengan try-catch
async function fetchUserData(userId) {
    try {
        const user = await fetchUser(userId);
        
        if (!user) {
            throw new Error("User not found");
        }
        
        const profile = await fetchUserProfile(user.id);
        const posts = await fetchUserPosts(user.id);
        
        return { user, profile, posts };
        
    } catch (error) {
        console.error("Error in fetchUserData:", error.message);
        
        // Return default data or re-throw
        if (error.message === "User not found") {
            return { user: null, profile: null, posts: [] };
        }
        
        throw error;
    }
}

// ✅ Multiple try-catch blocks
async function complexOperation() {
    try {
        const data = await fetchData();
        
        try {
            const processed = await processData(data);
            return processed;
        } catch (processError) {
            console.error("Processing failed:", processError.message);
            return data; // Return raw data as fallback
        }
        
    } catch (fetchError) {
        console.error("Fetch failed:", fetchError.message);
        throw fetchError;
    }
}

// ✅ Error handling dengan custom error types
async function validateAndProcess(userData) {
    try {
        // Validate user data
        if (!userData.name) {
            throw new ValidationError("Name is required");
        }
        
        if (!userData.email) {
            throw new ValidationError("Email is required");
        }
        
        // Process user data
        const result = await processUser(userData);
        return result;
        
    } catch (error) {
        if (error instanceof ValidationError) {
            console.error("Validation error:", error.message);
            return { success: false, error: error.message };
        }
        
        console.error("Processing error:", error.message);
        throw error;
    }
}
```

### 🔄 Parallel vs Sequential Execution
```javascript
// ✅ Sequential execution (satu per satu)
async function processSequential(items) {
    const results = [];
    
    for (let item of items) {
        const result = await processItem(item);
        results.push(result);
    }
    
    return results;
}

// ✅ Parallel execution (bersamaan)
async function processParallel(items) {
    const promises = items.map(item => processItem(item));
    return await Promise.all(promises);
}

// ✅ Mixed approach
async function processMixed(items) {
    const results = [];
    
    // Process in batches of 3
    for (let i = 0; i < items.length; i += 3) {
        const batch = items.slice(i, i + 3);
        const batchPromises = batch.map(item => processItem(item));
        const batchResults = await Promise.all(batchPromises);
        results.push(...batchResults);
    }
    
    return results;
}

// ✅ Comparison
async function compareApproaches() {
    const items = [1, 2, 3, 4, 5];
    
    console.time("Sequential");
    await processSequential(items);
    console.timeEnd("Sequential");
    
    console.time("Parallel");
    await processParallel(items);
    console.timeEnd("Parallel");
}
```

## 5. Event Loop

### 🔄 Single-threaded Nature
```javascript
// ✅ JavaScript adalah single-threaded
console.log("Start");

setTimeout(() => {
    console.log("Timeout 1");
}, 0);

setTimeout(() => {
    console.log("Timeout 2");
}, 0);

console.log("End");

// Output:
// "Start"
// "End"
// "Timeout 1"
// "Timeout 2"
```

### 🔄 Call Stack
```javascript
// ✅ Call stack demonstration
function first() {
    console.log("First function");
    second();
}

function second() {
    console.log("Second function");
    third();
}

function third() {
    console.log("Third function");
}

first();

// Call stack:
// third()
// second()
// first()
// main()
```

### 🔄 Web APIs
```javascript
// ✅ Web APIs berjalan di background
console.log("Start");

// setTimeout adalah Web API
setTimeout(() => {
    console.log("Timeout completed");
}, 1000);

// fetch adalah Web API
fetch('/api/data')
    .then(response => response.json())
    .then(data => console.log("Data:", data));

console.log("End");

// Web APIs yang umum:
// - setTimeout/setInterval
// - fetch
// - DOM events
// - File API
// - Geolocation API
```

### 🔄 Callback Queue
```javascript
// ✅ Callback queue demonstration
console.log("Start");

setTimeout(() => {
    console.log("Timeout 1");
}, 0);

setTimeout(() => {
    console.log("Timeout 2");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise 1");
});

Promise.resolve().then(() => {
    console.log("Promise 2");
});

console.log("End");

// Output:
// "Start"
// "End"
// "Promise 1"
// "Promise 2"
// "Timeout 1"
// "Timeout 2"
```

### 🔄 Microtask Queue
```javascript
// ✅ Microtask queue (Promise callbacks)
console.log("Start");

setTimeout(() => {
    console.log("Macrotask 1");
}, 0);

Promise.resolve().then(() => {
    console.log("Microtask 1");
});

Promise.resolve().then(() => {
    console.log("Microtask 2");
});

setTimeout(() => {
    console.log("Macrotask 2");
}, 0);

console.log("End");

// Output:
// "Start"
// "End"
// "Microtask 1"
// "Microtask 2"
// "Macrotask 1"
// "Macrotask 2"
```

## 6. Common Async Patterns

### 🔄 API Calls
```javascript
// ✅ Basic API call dengan fetch
async function fetchUser(userId) {
    try {
        const response = await fetch(`/api/users/${userId}`);
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        return await response.json();
    } catch (error) {
        console.error("Error fetching user:", error.message);
        throw error;
    }
}

// ✅ API call dengan timeout
async function fetchWithTimeout(url, timeout = 5000) {
    const controller = new AbortController();
    const timeoutId = setTimeout(() => controller.abort(), timeout);
    
    try {
        const response = await fetch(url, {
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

// ✅ Multiple API calls
async function fetchUserData(userId) {
    const [user, posts, followers] = await Promise.all([
        fetchUser(userId),
        fetchUserPosts(userId),
        fetchUserFollowers(userId)
    ]);
    
    return { user, posts, followers };
}
```

### 🔄 File Operations
```javascript
// ✅ File reading dengan async
async function readFileAsync(filename) {
    return new Promise((resolve, reject) => {
        // Simulate file reading
        setTimeout(() => {
            if (filename === "error.txt") {
                reject(new Error("File not found"));
            } else {
                resolve(`Content of ${filename}`);
            }
        }, 1000);
    });
}

// ✅ File operations dengan error handling
async function processFile(filename) {
    try {
        const content = await readFileAsync(filename);
        const processed = await processContent(content);
        return processed;
    } catch (error) {
        console.error("File processing failed:", error.message);
        return null;
    }
}

// ✅ Multiple file operations
async function processMultipleFiles(filenames) {
    const promises = filenames.map(filename => readFileAsync(filename));
    
    try {
        const contents = await Promise.all(promises);
        return contents;
    } catch (error) {
        console.error("Some files failed to read:", error.message);
        throw error;
    }
}
```

### 🔄 Database Queries
```javascript
// ✅ Database query dengan async
async function queryDatabase(sql, params = []) {
    return new Promise((resolve, reject) => {
        // Simulate database query
        setTimeout(() => {
            if (sql.includes("SELECT")) {
                resolve([
                    { id: 1, name: "Budi" },
                    { id: 2, name: "Ani" }
                ]);
            } else {
                reject(new Error("Database error"));
            }
        }, 500);
    });
}

// ✅ Database operations
async function getUserById(userId) {
    try {
        const users = await queryDatabase(
            "SELECT * FROM users WHERE id = ?",
            [userId]
        );
        
        return users[0] || null;
    } catch (error) {
        console.error("Database query failed:", error.message);
        throw error;
    }
}

// ✅ Transaction-like operations
async function createUserWithProfile(userData, profileData) {
    try {
        const user = await queryDatabase(
            "INSERT INTO users (name, email) VALUES (?, ?)",
            [userData.name, userData.email]
        );
        
        const profile = await queryDatabase(
            "INSERT INTO profiles (user_id, bio) VALUES (?, ?)",
            [user.id, profileData.bio]
        );
        
        return { user, profile };
    } catch (error) {
        console.error("User creation failed:", error.message);
        // Rollback logic would go here
        throw error;
    }
}
```

### 🔄 Timer Functions
```javascript
// ✅ setTimeout dengan Promise
function delay(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

// ✅ Usage
async function delayedOperation() {
    console.log("Start");
    await delay(2000);
    console.log("After 2 seconds");
}

// ✅ setInterval dengan Promise
function interval(ms, callback) {
    return new Promise((resolve, reject) => {
        const intervalId = setInterval(() => {
            try {
                const result = callback();
                if (result === false) {
                    clearInterval(intervalId);
                    resolve();
                }
            } catch (error) {
                clearInterval(intervalId);
                reject(error);
            }
        }, ms);
    });
}

// ✅ Usage
async function pollForData() {
    let attempts = 0;
    
    await interval(1000, () => {
        attempts++;
        console.log(`Attempt ${attempts}`);
        
        if (attempts >= 5) {
            return false; // Stop polling
        }
        
        return true; // Continue polling
    });
    
    console.log("Polling completed");
}
```

## 7. Best Practices

### 🛡️ Avoid Callback Hell
```javascript
// ❌ Callback hell
function processData(data, callback) {
    validateData(data, function(error, validatedData) {
        if (error) {
            callback(error);
        } else {
            transformData(validatedData, function(error, transformedData) {
                if (error) {
                    callback(error);
                } else {
                    saveData(transformedData, function(error, savedData) {
                        if (error) {
                            callback(error);
                        } else {
                            callback(null, savedData);
                        }
                    });
                }
            });
        }
    });
}

// ✅ Solusi dengan Promise
async function processData(data) {
    try {
        const validatedData = await validateData(data);
        const transformedData = await transformData(validatedData);
        const savedData = await saveData(transformedData);
        return savedData;
    } catch (error) {
        console.error("Processing failed:", error.message);
        throw error;
    }
}
```

### 🔒 Proper Error Handling
```javascript
// ✅ Comprehensive error handling
async function robustOperation() {
    try {
        const data = await fetchData();
        
        if (!data) {
            throw new Error("No data received");
        }
        
        const processed = await processData(data);
        return processed;
        
    } catch (error) {
        // Log error for debugging
        console.error("Operation failed:", error);
        
        // Handle specific error types
        if (error.name === 'NetworkError') {
            return { error: 'Network connection failed' };
        }
        
        if (error.name === 'ValidationError') {
            return { error: 'Invalid data provided' };
        }
        
        // Re-throw unknown errors
        throw error;
    }
}

// ✅ Error boundaries
async function safeAsyncOperation() {
    try {
        return await riskyOperation();
    } catch (error) {
        console.error("Operation failed, using fallback:", error.message);
        return fallbackOperation();
    }
}
```

### 🔄 Promise Rejection Handling
```javascript
// ✅ Handle unhandled promise rejections
process.on('unhandledRejection', (reason, promise) => {
    console.error('Unhandled Rejection at:', promise, 'reason:', reason);
});

// ✅ Always handle promise rejections
async function safePromiseOperation() {
    try {
        const result = await riskyPromise();
        return result;
    } catch (error) {
        console.error("Promise rejected:", error.message);
        return null;
    }
}

// ✅ Promise rejection dalam loops
async function processItemsSafely(items) {
    const results = [];
    
    for (let item of items) {
        try {
            const result = await processItem(item);
            results.push(result);
        } catch (error) {
            console.error(`Failed to process item ${item}:`, error.message);
            results.push(null); // Keep array length consistent
        }
    }
    
    return results;
}
```

### 📝 Async Function Naming
```javascript
// ✅ Clear async function naming
async function fetchUserData(userId) {
    // Function name indicates it's async and fetches data
}

async function processUserAsync(user) {
    // Suffix indicates it's async
}

async function getUserById(id) {
    // Clear what it does
}

// ✅ Consistent error handling
async function fetchUserData(userId) {
    try {
        const response = await fetch(`/api/users/${userId}`);
        
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}: ${response.statusText}`);
        }
        
        return await response.json();
    } catch (error) {
        console.error(`Failed to fetch user ${userId}:`, error.message);
        throw error;
    }
}
```

## 8. Studi Kasus Praktis

### 🛒 E-commerce Async Operations
```javascript
// ✅ E-commerce async operations
class EcommerceAPI {
    async fetchProducts(category = null) {
        try {
            const url = category 
                ? `/api/products?category=${category}`
                : '/api/products';
                
            const response = await fetch(url);
            
            if (!response.ok) {
                throw new Error(`Failed to fetch products: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error("Error fetching products:", error.message);
            throw error;
        }
    }
    
    async createOrder(orderData) {
        try {
            // Validate order data
            this.validateOrder(orderData);
            
            // Process payment
            const paymentResult = await this.processPayment(orderData.payment);
            
            // Create order
            const order = await this.saveOrder(orderData);
            
            // Update inventory
            await this.updateInventory(orderData.items);
            
            // Send confirmation email
            await this.sendOrderConfirmation(order.id, orderData.customer.email);
            
            return order;
            
        } catch (error) {
            console.error("Order creation failed:", error.message);
            
            // Rollback if needed
            await this.rollbackOrder(orderData);
            
            throw error;
        }
    }
    
    async processPayment(paymentData) {
        const response = await fetch('/api/payments', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(paymentData)
        });
        
        if (!response.ok) {
            throw new Error(`Payment failed: ${response.status}`);
        }
        
        return await response.json();
    }
    
    async updateInventory(items) {
        const promises = items.map(item => 
            fetch(`/api/inventory/${item.productId}`, {
                method: 'PATCH',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ 
                    quantity: -item.quantity 
                })
            })
        );
        
        await Promise.all(promises);
    }
    
    async sendOrderConfirmation(orderId, email) {
        try {
            await fetch('/api/emails/order-confirmation', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ orderId, email })
            });
        } catch (error) {
            console.warn("Failed to send confirmation email:", error.message);
            // Don't throw error for email failure
        }
    }
    
    validateOrder(orderData) {
        if (!orderData.items || orderData.items.length === 0) {
            throw new Error("Order must contain at least one item");
        }
        
        if (!orderData.customer || !orderData.customer.email) {
            throw new Error("Valid customer information is required");
        }
        
        if (!orderData.payment) {
            throw new Error("Payment information is required");
        }
    }
    
    async rollbackOrder(orderData) {
        console.log("Rolling back order creation...");
        // Implement rollback logic
    }
}

// ✅ Usage
const api = new EcommerceAPI();

async function placeOrder() {
    try {
        const orderData = {
            items: [
                { productId: "P001", quantity: 2 },
                { productId: "P002", quantity: 1 }
            ],
            customer: {
                email: "budi@email.com",
                name: "Budi"
            },
            payment: {
                method: "credit_card",
                cardNumber: "1234567890123456"
            }
        };
        
        const order = await api.createOrder(orderData);
        console.log("Order created:", order);
        
    } catch (error) {
        console.error("Failed to place order:", error.message);
    }
}
```

### 🎮 Game Async Operations
```javascript
// ✅ Game async operations
class GameAPI {
    async saveGameState(gameState) {
        try {
            const response = await fetch('/api/game/save', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(gameState)
            });
            
            if (!response.ok) {
                throw new Error(`Failed to save game: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error("Save game failed:", error.message);
            throw error;
        }
    }
    
    async loadGameState(gameId) {
        try {
            const response = await fetch(`/api/game/${gameId}`);
            
            if (!response.ok) {
                throw new Error(`Failed to load game: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error("Load game failed:", error.message);
            throw error;
        }
    }
    
    async syncWithServer(localState) {
        try {
            // Send local state to server
            const response = await fetch('/api/game/sync', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(localState)
            });
            
            if (!response.ok) {
                throw new Error(`Sync failed: ${response.status}`);
            }
            
            const serverState = await response.json();
            
            // Merge local and server state
            return this.mergeGameStates(localState, serverState);
            
        } catch (error) {
            console.error("Sync failed:", error.message);
            return localState; // Use local state as fallback
        }
    }
    
    mergeGameStates(local, server) {
        // Implement merge logic
        return {
            ...server,
            localChanges: local.localChanges,
            lastSync: new Date()
        };
    }
    
    async fetchLeaderboard() {
        try {
            const response = await fetch('/api/leaderboard');
            
            if (!response.ok) {
                throw new Error(`Failed to fetch leaderboard: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error("Leaderboard fetch failed:", error.message);
            return []; // Return empty array as fallback
        }
    }
    
    async submitScore(score) {
        try {
            const response = await fetch('/api/scores', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(score)
            });
            
            if (!response.ok) {
                throw new Error(`Failed to submit score: ${response.status}`);
            }
            
            return await response.json();
        } catch (error) {
            console.error("Score submission failed:", error.message);
            // Queue for retry later
            this.queueForRetry('submitScore', score);
        }
    }
    
    queueForRetry(operation, data) {
        const retryQueue = JSON.parse(localStorage.getItem('retryQueue') || '[]');
        retryQueue.push({ operation, data, timestamp: Date.now() });
        localStorage.setItem('retryQueue', JSON.stringify(retryQueue));
    }
}

// ✅ Usage
const gameAPI = new GameAPI();

async function saveAndSyncGame(gameState) {
    try {
        // Save locally first
        localStorage.setItem('gameState', JSON.stringify(gameState));
        
        // Try to save to server
        await gameAPI.saveGameState(gameState);
        
        // Sync with server
        const syncedState = await gameAPI.syncWithServer(gameState);
        
        // Update local state with synced data
        localStorage.setItem('gameState', JSON.stringify(syncedState));
        
        console.log("Game saved and synced successfully");
        
    } catch (error) {
        console.error("Save/sync failed:", error.message);
        // Game state is still saved locally
    }
}
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Async Programming](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous)
- **JavaScript.info**: [Promises](https://javascript.info/promise-basics)
- **W3Schools**: [JavaScript Async](https://www.w3schools.com/js/js_async.asp)

### 📖 Buku Rekomendasi
- "Eloquent JavaScript" by Marijn Haverbeke
- "You Don't Know JS: Async & Performance" by Kyle Simpson
- "JavaScript: The Definitive Guide" by David Flanagan

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Async/Await Tutorial
- **The Net Ninja**: JavaScript Promises & Async/Await
- **Programming with Mosh**: JavaScript Async Programming

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen async programming
- **JSFiddle**: Untuk testing promises dan async/await
- **Replit**: Untuk project async programming
- **Browser DevTools**: Untuk debugging async code

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan setTimeout dan callbacks
2. **Learn Promises**: Kuasai Promise dan .then()/.catch()
3. **Master Async/Await**: Pelajari syntax modern
4. **Understand Event Loop**: Pahami cara JavaScript menangani async
5. **Build Projects**: Aplikasikan dalam project nyata

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep async programming
2. **Practice** → Tulis kode dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki
5. **Repeat** → Ulangi dengan konsep async baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Async Programming
- **freeCodeCamp**: JavaScript Promises and Async/Await
- **Scrimba**: Async programming tutorials
- **JavaScript30**: Async-based challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Forgetting await
async function fetchData() {
    const response = fetch('/api/data');  // ❌ Missing await
    return response.json();
}

// ✅ Solusi: Selalu gunakan await
async function fetchData() {
    const response = await fetch('/api/data');  // ✅ With await
    return response.json();
}

// ❌ Not handling promise rejections
async function riskyOperation() {
    const result = await someAsyncOperation();
    return result;  // ❌ No error handling
}

// ✅ Solusi: Selalu handle errors
async function safeOperation() {
    try {
        const result = await someAsyncOperation();
        return result;
    } catch (error) {
        console.error("Operation failed:", error.message);
        throw error;
    }
}

// ❌ Blocking the event loop
async function heavyOperation() {
    for (let i = 0; i < 1000000; i++) {
        // Heavy computation
    }
}

// ✅ Solusi: Use setTimeout untuk non-blocking
async function nonBlockingOperation() {
    for (let i = 0; i < 1000000; i++) {
        if (i % 1000 === 0) {
            await new Promise(resolve => setTimeout(resolve, 0));
        }
        // Heavy computation
    }
}
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.log untuk debugging async
async function debugAsync() {
    console.log("Starting async operation");
    
    try {
        const result = await someAsyncOperation();
        console.log("Async operation completed:", result);
        return result;
    } catch (error) {
        console.error("Async operation failed:", error);
        throw error;
    }
}

// ✅ Gunakan Promise.allSettled untuk debugging
async function debugMultiplePromises() {
    const promises = [
        fetch('/api/users'),
        fetch('/api/posts'),
        fetch('/api/comments')
    ];
    
    const results = await Promise.allSettled(promises);
    
    results.forEach((result, index) => {
        if (result.status === 'fulfilled') {
            console.log(`Promise ${index} succeeded:`, result.value);
        } else {
            console.error(`Promise ${index} failed:`, result.reason);
        }
    });
}

// ✅ Gunakan async stack traces
async function asyncFunction() {
    await someAsyncOperation();
}

// Enable async stack traces in Node.js
process.on('unhandledRejection', (reason, promise) => {
    console.error('Unhandled Rejection at:', promise, 'reason:', reason);
});
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Async Generators
```javascript
// ✅ Async generator untuk streaming data
async function* asyncGenerator() {
    for (let i = 0; i < 5; i++) {
        await new Promise(resolve => setTimeout(resolve, 1000));
        yield i;
    }
}

// ✅ Usage
async function consumeAsyncGenerator() {
    for await (let value of asyncGenerator()) {
        console.log(value);
    }
}
```

### 🔄 Async Iterators
```javascript
// ✅ Async iterator
class AsyncDataStream {
    constructor(data) {
        this.data = data;
        this.index = 0;
    }
    
    async *[Symbol.asyncIterator]() {
        for (let item of this.data) {
            await new Promise(resolve => setTimeout(resolve, 100));
            yield item;
        }
    }
}

// ✅ Usage
async function processAsyncStream() {
    const stream = new AsyncDataStream([1, 2, 3, 4, 5]);
    
    for await (let value of stream) {
        console.log(value);
    }
}
```

### 🔄 Async Context
```javascript
// ✅ Async context untuk tracking
class AsyncContext {
    constructor() {
        this.context = new Map();
    }
    
    set(key, value) {
        this.context.set(key, value);
    }
    
    get(key) {
        return this.context.get(key);
    }
    
    async run(fn) {
        return await fn();
    }
}

// ✅ Usage
const context = new AsyncContext();

async function asyncOperation() {
    context.set('userId', 123);
    
    await context.run(async () => {
        const userId = context.get('userId');
        console.log('Processing user:', userId);
    });
}
```

---

> **💡 Pro Tip**: Async programming adalah kunci untuk aplikasi modern yang responsif. Kuasai Promise dan async/await untuk membuat kode yang efisien dan mudah dipahami! 