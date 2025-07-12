# 🎯 Objects Fundamental

## 1. Apa itu Object?

**Object** adalah struktur data yang menyimpan data dalam format key-value pairs. Bayangkan object seperti kartu identitas - setiap properti (key) memiliki nilai (value) yang spesifik.

### 🎯 Konsep Dasar
- **Property**: Pasangan key-value dalam object
- **Method**: Function yang menjadi property object
- **Key**: Identifier untuk mengakses value
- **Value**: Data yang disimpan (bisa berbagai tipe)
- **Reference**: Object disimpan sebagai reference, bukan copy

### 📝 Contoh Sederhana
```javascript
// Object sederhana
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// Mengakses property
console.log(person.name);     // "Budi"
console.log(person["age"]);   // 25
console.log(person.city);     // "Jakarta"
```

### 🔍 Istilah Penting
- **Property**: Pasangan key-value
- **Method**: Function dalam object
- **Key**: Nama property
- **Value**: Nilai property
- **Reference**: Pointer ke object di memory
- **Prototype**: Template untuk object

## 2. Membuat dan Mengakses Object

### 🔧 Object Literal Syntax
```javascript
// ✅ Object literal (cara paling umum)
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// ✅ Object dengan berbagai tipe data
let mixedObject = {
    string: "Hello",
    number: 42,
    boolean: true,
    null: null,
    undefined: undefined,
    array: [1, 2, 3],
    nestedObject: { key: "value" },
    function: function() { return "Hello"; }
};

// ✅ Object dengan computed property names
let propertyName = "dynamicKey";
let dynamicObject = {
    [propertyName]: "Dynamic value",
    [`computed_${propertyName}`]: "Computed value"
};
```

### 🏗️ Object Constructor
```javascript
// ✅ Object constructor
let person = new Object();
person.name = "Budi";
person.age = 25;

// ✅ Object.create() dengan prototype
let animal = {
    makeSound() {
        console.log("Some sound");
    }
};

let dog = Object.create(animal);
dog.name = "Buddy";
dog.makeSound();  // "Some sound"

// ✅ Object.assign() untuk menggabungkan objects
let target = { a: 1 };
let source1 = { b: 2 };
let source2 = { c: 3 };

let result = Object.assign(target, source1, source2);
console.log(result);  // { a: 1, b: 2, c: 3 }
```

### 📍 Property Access
```javascript
let person = {
    name: "Budi",
    age: 25,
    "favorite-color": "blue"  // Property dengan hyphen
};

// ✅ Dot notation
console.log(person.name);  // "Budi"
console.log(person.age);   // 25

// ✅ Bracket notation
console.log(person["name"]);           // "Budi"
console.log(person["favorite-color"]); // "blue" (harus bracket)

// ✅ Dynamic property access
let propertyName = "age";
console.log(person[propertyName]);  // 25

// ✅ Nested property access
let user = {
    profile: {
        name: "Budi",
        address: {
            city: "Jakarta",
            country: "Indonesia"
        }
    }
};

console.log(user.profile.name);                    // "Budi"
console.log(user.profile.address.city);            // "Jakarta"
console.log(user["profile"]["address"]["country"]); // "Indonesia"
```

### 🔍 Property Descriptors
```javascript
// ✅ Property descriptor
let obj = {};

Object.defineProperty(obj, "readOnly", {
    value: "Cannot change",
    writable: false,
    enumerable: true,
    configurable: false
});

// ✅ Getter dan setter
let person = {
    firstName: "Budi",
    lastName: "Santoso",
    
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    
    set fullName(value) {
        [this.firstName, this.lastName] = value.split(" ");
    }
};

console.log(person.fullName);  // "Budi Santoso"
person.fullName = "Ani Wijaya";
console.log(person.firstName); // "Ani"
```

## 3. Object Properties

### ➕ Adding Properties
```javascript
let person = { name: "Budi" };

// ✅ Menambah property baru
person.age = 25;
person.city = "Jakarta";

// ✅ Menambah property dengan bracket notation
person["favorite-color"] = "blue";
person["phone number"] = "08123456789";

// ✅ Menambah property dengan Object.defineProperty
Object.defineProperty(person, "id", {
    value: "P001",
    writable: false,
    enumerable: true
});

// ✅ Menambah multiple properties
Object.assign(person, {
    email: "budi@email.com",
    isActive: true
});
```

### 🔄 Updating Properties
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// ✅ Update dengan dot notation
person.age = 26;
person.city = "Bandung";

// ✅ Update dengan bracket notation
person["name"] = "Budi Santoso";

// ✅ Update dengan Object.assign
Object.assign(person, {
    age: 27,
    email: "budi@email.com"
});

// ✅ Update nested properties
person.address = {
    city: "Jakarta",
    country: "Indonesia"
};
person.address.city = "Bandung";
```

### ➖ Deleting Properties
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta",
    tempProperty: "Will be deleted"
};

// ✅ Delete dengan delete operator
delete person.tempProperty;
delete person["age"];

// ✅ Delete dengan Object.defineProperty (configurable: true)
Object.defineProperty(person, "deletable", {
    value: "Can be deleted",
    configurable: true
});
delete person.deletable;  // ✅ Works

// ✅ Delete dengan Object.defineProperty (configurable: false)
Object.defineProperty(person, "nonDeletable", {
    value: "Cannot be deleted",
    configurable: false
});
delete person.nonDeletable;  // ❌ Won't work

// ✅ Check if property exists
console.log("name" in person);        // true
console.log(person.hasOwnProperty("name")); // true
```

### 🔍 Property Descriptors
```javascript
// ✅ Property descriptor attributes
let obj = {};

Object.defineProperty(obj, "readOnly", {
    value: "Cannot change",
    writable: false,      // Tidak bisa diubah
    enumerable: true,     // Muncul dalam loop
    configurable: false   // Tidak bisa dihapus
});

// ✅ Getter dan setter
let person = {
    _age: 25,
    
    get age() {
        return this._age;
    },
    
    set age(value) {
        if (value >= 0 && value <= 150) {
            this._age = value;
        } else {
            throw new Error("Invalid age");
        }
    }
};

console.log(person.age);  // 25
person.age = 30;         // ✅ Works
// person.age = -5;      // ❌ Error
```

## 4. Object Methods

### 🔧 Method Definition
```javascript
let calculator = {
    // ✅ Method dengan function declaration
    add: function(a, b) {
        return a + b;
    },
    
    // ✅ Method shorthand (ES6+)
    subtract(a, b) {
        return a - b;
    },
    
    // ✅ Arrow function sebagai method
    multiply: (a, b) => a * b,
    
    // ✅ Method dengan default parameters
    divide(a, b = 1) {
        return a / b;
    }
};

console.log(calculator.add(5, 3));      // 8
console.log(calculator.subtract(10, 4)); // 6
console.log(calculator.multiply(2, 6));  // 12
console.log(calculator.divide(10, 2));   // 5
```

### 🎯 This Keyword
```javascript
let person = {
    name: "Budi",
    age: 25,
    
    // ✅ Method dengan this
    greet() {
        return `Hello, my name is ${this.name}`;
    },
    
    // ✅ Method yang mengubah property
    birthday() {
        this.age++;
        return `Happy birthday! You are now ${this.age} years old.`;
    },
    
    // ✅ Method dengan parameter
    introduce(otherName) {
        return `Hi ${otherName}, I'm ${this.name}`;
    }
};

console.log(person.greet());           // "Hello, my name is Budi"
console.log(person.birthday());        // "Happy birthday! You are now 26 years old."
console.log(person.introduce("Ani"));  // "Hi Ani, I'm Budi"
```

### ⚠️ Arrow Functions dalam Object
```javascript
let person = {
    name: "Budi",
    age: 25,
    
    // ❌ Arrow function tidak memiliki this yang benar
    greetArrow: () => {
        return `Hello, my name is ${this.name}`;  // this.name = undefined
    },
    
    // ✅ Regular function memiliki this yang benar
    greetRegular() {
        return `Hello, my name is ${this.name}`;
    },
    
    // ✅ Arrow function dalam method
    greetWithArrow() {
        setTimeout(() => {
            console.log(`Hello from ${this.name}`);  // ✅ this works
        }, 1000);
    }
};

console.log(person.greetArrow());    // "Hello, my name is undefined"
console.log(person.greetRegular());  // "Hello, my name is Budi"
```

### 🔄 Method Chaining
```javascript
let calculator = {
    value: 0,
    
    add(num) {
        this.value += num;
        return this;  // Return this untuk chaining
    },
    
    subtract(num) {
        this.value -= num;
        return this;
    },
    
    multiply(num) {
        this.value *= num;
        return this;
    },
    
    divide(num) {
        this.value /= num;
        return this;
    },
    
    getResult() {
        return this.value;
    }
};

// ✅ Method chaining
let result = calculator
    .add(10)
    .multiply(2)
    .subtract(5)
    .divide(3)
    .getResult();

console.log(result);  // 5
```

## 5. Object Destructuring

### 🔗 Basic Destructuring
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta",
    email: "budi@email.com"
};

// ✅ Basic destructuring
let { name, age } = person;
console.log(name);  // "Budi"
console.log(age);   // 25

// ✅ Destructuring dengan alias
let { name: userName, age: userAge } = person;
console.log(userName);  // "Budi"
console.log(userAge);   // 25

// ✅ Destructuring dengan default values
let { name, age, country = "Indonesia" } = person;
console.log(country);  // "Indonesia"
```

### 🔗 Nested Destructuring
```javascript
let user = {
    name: "Budi",
    profile: {
        age: 25,
        address: {
            city: "Jakarta",
            country: "Indonesia"
        }
    },
    preferences: {
        theme: "dark",
        language: "id"
    }
};

// ✅ Nested destructuring
let { 
    name, 
    profile: { age, address: { city } },
    preferences: { theme }
} = user;

console.log(name);  // "Budi"
console.log(age);   // 25
console.log(city);  // "Jakarta"
console.log(theme); // "dark"

// ✅ Destructuring dengan alias untuk nested
let { 
    profile: { address: { city: userCity } }
} = user;
console.log(userCity);  // "Jakarta"
```

### 🔗 Destructuring dalam Function Parameters
```javascript
// ✅ Function dengan destructured parameters
function processUser({ name, age, email = "default@email.com" }) {
    console.log(`Processing user: ${name}, age: ${age}, email: ${email}`);
}

let user = { name: "Budi", age: 25 };
processUser(user);  // "Processing user: Budi, age: 25, email: default@email.com"

// ✅ Function dengan nested destructuring
function processAddress({ 
    profile: { 
        address: { city, country } 
    } 
}) {
    console.log(`User lives in ${city}, ${country}`);
}

let userWithAddress = {
    profile: {
        address: {
            city: "Jakarta",
            country: "Indonesia"
        }
    }
};

processAddress(userWithAddress);  // "User lives in Jakarta, Indonesia"
```

## 6. Object Methods Built-in

### 🔍 Object.keys()
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// ✅ Object.keys() - mendapatkan array of keys
let keys = Object.keys(person);
console.log(keys);  // ["name", "age", "city"]

// ✅ Iterasi dengan keys
keys.forEach(key => {
    console.log(`${key}: ${person[key]}`);
});

// ✅ Check if object has properties
if (Object.keys(person).length === 0) {
    console.log("Object is empty");
}
```

### 🔍 Object.values()
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// ✅ Object.values() - mendapatkan array of values
let values = Object.values(person);
console.log(values);  // ["Budi", 25, "Jakarta"]

// ✅ Sum all numeric values
let scores = { math: 85, science: 90, english: 88 };
let totalScore = Object.values(scores).reduce((sum, score) => sum + score, 0);
console.log(totalScore);  // 263
```

### 🔍 Object.entries()
```javascript
let person = {
    name: "Budi",
    age: 25,
    city: "Jakarta"
};

// ✅ Object.entries() - mendapatkan array of [key, value] pairs
let entries = Object.entries(person);
console.log(entries);  // [["name", "Budi"], ["age", 25], ["city", "Jakarta"]]

// ✅ Iterasi dengan entries
entries.forEach(([key, value]) => {
    console.log(`${key}: ${value}`);
});

// ✅ Convert entries back to object
let newPerson = Object.fromEntries(entries);
console.log(newPerson);  // { name: "Budi", age: 25, city: "Jakarta" }
```

### 🔍 Object.assign()
```javascript
// ✅ Object.assign() - menggabungkan objects
let target = { a: 1, b: 2 };
let source1 = { b: 3, c: 4 };
let source2 = { d: 5 };

let result = Object.assign(target, source1, source2);
console.log(result);  // { a: 1, b: 3, c: 4, d: 5 }
console.log(target);  // { a: 1, b: 3, c: 4, d: 5 } (target berubah)

// ✅ Object.assign() dengan empty object (immutable)
let original = { name: "Budi", age: 25 };
let updated = Object.assign({}, original, { age: 26 });
console.log(original);  // { name: "Budi", age: 25 } (tidak berubah)
console.log(updated);   // { name: "Budi", age: 26 }
```

### 🔍 Object.freeze()
```javascript
let person = {
    name: "Budi",
    age: 25
};

// ✅ Object.freeze() - membuat object immutable
Object.freeze(person);

// ❌ Tidak bisa mengubah property
// person.age = 26;  // Error in strict mode

// ❌ Tidak bisa menambah property
// person.city = "Jakarta";  // Error in strict mode

// ❌ Tidak bisa menghapus property
// delete person.name;  // Error in strict mode

// ✅ Check if object is frozen
console.log(Object.isFrozen(person));  // true
```

## 7. Object-oriented Basics

### 🏗️ Classes vs Objects
```javascript
// ✅ Class definition (ES6+)
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, my name is ${this.name}`;
    }
    
    birthday() {
        this.age++;
        return `Happy birthday! You are now ${this.age} years old.`;
    }
}

// ✅ Creating objects from class
let person1 = new Person("Budi", 25);
let person2 = new Person("Ani", 30);

console.log(person1.greet());  // "Hello, my name is Budi"
console.log(person2.birthday()); // "Happy birthday! You are now 31 years old."
```

### 🔄 Inheritance Concept
```javascript
// ✅ Base class
class Animal {
    constructor(name) {
        this.name = name;
    }
    
    makeSound() {
        return "Some sound";
    }
    
    introduce() {
        return `I am ${this.name}`;
    }
}

// ✅ Derived class
class Dog extends Animal {
    constructor(name, breed) {
        super(name);  // Call parent constructor
        this.breed = breed;
    }
    
    makeSound() {
        return "Woof!";
    }
    
    fetch() {
        return `${this.name} is fetching the ball`;
    }
}

// ✅ Using inheritance
let dog = new Dog("Buddy", "Golden Retriever");
console.log(dog.introduce());  // "I am Buddy" (from parent)
console.log(dog.makeSound());  // "Woof!" (overridden)
console.log(dog.fetch());      // "Buddy is fetching the ball" (new method)
```

### 🔒 Encapsulation
```javascript
// ✅ Encapsulation dengan private fields (ES2022)
class BankAccount {
    #balance = 0;  // Private field
    #accountNumber;
    
    constructor(accountNumber, initialBalance = 0) {
        this.#accountNumber = accountNumber;
        this.#balance = initialBalance;
    }
    
    // Public methods
    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
            return `Deposited ${amount}. New balance: ${this.#balance}`;
        }
        return "Invalid amount";
    }
    
    withdraw(amount) {
        if (amount > 0 && amount <= this.#balance) {
            this.#balance -= amount;
            return `Withdrawn ${amount}. New balance: ${this.#balance}`;
        }
        return "Insufficient funds or invalid amount";
    }
    
    getBalance() {
        return this.#balance;
    }
    
    getAccountNumber() {
        return this.#accountNumber;
    }
}

let account = new BankAccount("12345", 1000);
console.log(account.deposit(500));   // "Deposited 500. New balance: 1500"
console.log(account.withdraw(200));   // "Withdrawn 200. New balance: 1300"
console.log(account.getBalance());    // 1300
// console.log(account.#balance);    // ❌ Error - private field
```

### 🔄 Polymorphism
```javascript
// ✅ Polymorphism dengan method overriding
class Shape {
    area() {
        return 0;
    }
}

class Circle extends Shape {
    constructor(radius) {
        super();
        this.radius = radius;
    }
    
    area() {
        return Math.PI * this.radius * this.radius;
    }
}

class Rectangle extends Shape {
    constructor(width, height) {
        super();
        this.width = width;
        this.height = height;
    }
    
    area() {
        return this.width * this.height;
    }
}

// ✅ Polymorphic behavior
let shapes = [
    new Circle(5),
    new Rectangle(4, 6),
    new Circle(3)
];

shapes.forEach(shape => {
    console.log(`Area: ${shape.area().toFixed(2)}`);
});
```

## 8. Best Practices & Patterns

### 🛡️ Defensive Programming
```javascript
// ✅ Validasi object sebelum operasi
function processUser(user) {
    if (!user || typeof user !== 'object') {
        throw new Error('User must be a valid object');
    }
    
    if (!user.name || typeof user.name !== 'string') {
        throw new Error('User must have a valid name');
    }
    
    if (!user.age || typeof user.age !== 'number' || user.age < 0) {
        throw new Error('User must have a valid age');
    }
    
    return `Hello, ${user.name}! You are ${user.age} years old.`;
}

// ✅ Safe property access
function getUserName(user) {
    return user && user.name || "Anonymous";
}

// ✅ Deep property access
function getNestedValue(obj, path) {
    return path.split('.').reduce((current, key) => {
        return current && current[key] !== undefined ? current[key] : null;
    }, obj);
}

let user = {
    profile: {
        address: {
            city: "Jakarta"
        }
    }
};

console.log(getNestedValue(user, 'profile.address.city'));  // "Jakarta"
console.log(getNestedValue(user, 'profile.address.country')); // null
```

### 🔒 Immutability
```javascript
// ✅ Immutable object operations
let originalPerson = { name: "Budi", age: 25 };

// ✅ Spread operator untuk copy
let updatedPerson = { ...originalPerson, age: 26 };
console.log(originalPerson);  // { name: "Budi", age: 25 } (tidak berubah)
console.log(updatedPerson);   // { name: "Budi", age: 26 }

// ✅ Object.assign untuk copy
let copiedPerson = Object.assign({}, originalPerson);
console.log(copiedPerson);  // { name: "Budi", age: 25 }

// ✅ Deep copy dengan JSON (untuk simple objects)
let deepCopy = JSON.parse(JSON.stringify(originalPerson));

// ✅ Immutable update patterns
let user = {
    name: "Budi",
    profile: {
        age: 25,
        address: {
            city: "Jakarta"
        }
    }
};

// ✅ Update nested object (immutable)
let updatedUser = {
    ...user,
    profile: {
        ...user.profile,
        address: {
            ...user.profile.address,
            city: "Bandung"
        }
    }
};
```

### 📊 Factory Pattern
```javascript
// ✅ Factory function untuk membuat objects
function createUser(name, age, email) {
    return {
        name,
        age,
        email,
        createdAt: new Date(),
        isActive: true,
        
        greet() {
            return `Hello, I'm ${this.name}`;
        },
        
        updateProfile(updates) {
            return { ...this, ...updates };
        },
        
        deactivate() {
            return { ...this, isActive: false };
        }
    };
}

// ✅ Factory dengan validation
function createProduct(name, price, category) {
    if (!name || typeof name !== 'string') {
        throw new Error('Product name is required and must be a string');
    }
    
    if (typeof price !== 'number' || price < 0) {
        throw new Error('Price must be a positive number');
    }
    
    if (!category || typeof category !== 'string') {
        throw new Error('Category is required and must be a string');
    }
    
    return {
        id: Date.now(),
        name,
        price,
        category,
        createdAt: new Date(),
        
        getFormattedPrice() {
            return `$${this.price.toFixed(2)}`;
        },
        
        applyDiscount(percentage) {
            const discount = this.price * (percentage / 100);
            return { ...this, price: this.price - discount };
        }
    };
}
```

## 9. Studi Kasus Praktis

### 🛒 E-commerce Product System
```javascript
// ✅ Product management system
class ProductManager {
    constructor() {
        this.products = new Map();
    }
    
    addProduct(product) {
        if (!product.id || !product.name || !product.price) {
            throw new Error('Product must have id, name, and price');
        }
        
        this.products.set(product.id, {
            ...product,
            createdAt: new Date(),
            isActive: true
        });
        
        return product.id;
    }
    
    getProduct(id) {
        const product = this.products.get(id);
        if (!product) {
            throw new Error('Product not found');
        }
        return { ...product };
    }
    
    updateProduct(id, updates) {
        const product = this.products.get(id);
        if (!product) {
            throw new Error('Product not found');
        }
        
        const updatedProduct = { ...product, ...updates };
        this.products.set(id, updatedProduct);
        
        return updatedProduct;
    }
    
    deleteProduct(id) {
        if (!this.products.has(id)) {
            throw new Error('Product not found');
        }
        
        this.products.delete(id);
        return true;
    }
    
    searchProducts(criteria) {
        const results = [];
        
        for (let [id, product] of this.products) {
            if (this.matchesCriteria(product, criteria)) {
                results.push({ id, ...product });
            }
        }
        
        return results;
    }
    
    matchesCriteria(product, criteria) {
        if (criteria.name && !product.name.toLowerCase().includes(criteria.name.toLowerCase())) {
            return false;
        }
        
        if (criteria.minPrice && product.price < criteria.minPrice) {
            return false;
        }
        
        if (criteria.maxPrice && product.price > criteria.maxPrice) {
            return false;
        }
        
        if (criteria.category && product.category !== criteria.category) {
            return false;
        }
        
        return true;
    }
    
    getProductsByCategory(category) {
        return this.searchProducts({ category });
    }
    
    getTotalValue() {
        let total = 0;
        for (let product of this.products.values()) {
            total += product.price;
        }
        return total;
    }
}

// ✅ Usage
const manager = new ProductManager();

manager.addProduct({
    id: "P001",
    name: "Laptop",
    price: 15000000,
    category: "Electronics"
});

manager.addProduct({
    id: "P002",
    name: "Mouse",
    price: 500000,
    category: "Electronics"
});

console.log(manager.getProductsByCategory("Electronics"));
console.log(manager.getTotalValue());
```

### 🎮 Game Character System
```javascript
// ✅ Game character system
class Character {
    constructor(name, characterClass) {
        this.name = name;
        this.characterClass = characterClass;
        this.level = 1;
        this.experience = 0;
        this.health = 100;
        this.maxHealth = 100;
        this.mana = 50;
        this.maxMana = 50;
        this.inventory = [];
        this.skills = [];
    }
    
    takeDamage(damage) {
        this.health = Math.max(0, this.health - damage);
        
        if (this.health === 0) {
            return { alive: false, message: `${this.name} has died!` };
        }
        
        return { alive: true, health: this.health };
    }
    
    heal(amount) {
        this.health = Math.min(this.maxHealth, this.health + amount);
        return this.health;
    }
    
    gainExperience(exp) {
        this.experience += exp;
        
        const requiredExp = this.level * 100;
        if (this.experience >= requiredExp) {
            this.levelUp();
        }
        
        return { level: this.level, experience: this.experience };
    }
    
    levelUp() {
        this.level++;
        this.experience -= (this.level - 1) * 100;
        this.maxHealth += 20;
        this.maxMana += 10;
        this.health = this.maxHealth;
        this.mana = this.maxMana;
        
        return {
            level: this.level,
            maxHealth: this.maxHealth,
            maxMana: this.maxMana
        };
    }
    
    addItem(item) {
        this.inventory.push(item);
        return this.inventory.length;
    }
    
    useItem(itemName) {
        const itemIndex = this.inventory.findIndex(item => item.name === itemName);
        
        if (itemIndex === -1) {
            return { success: false, message: "Item not found" };
        }
        
        const item = this.inventory[itemIndex];
        
        if (item.type === "healing") {
            this.heal(item.value);
        } else if (item.type === "mana") {
            this.mana = Math.min(this.maxMana, this.mana + item.value);
        }
        
        this.inventory.splice(itemIndex, 1);
        
        return { success: true, message: `Used ${itemName}` };
    }
    
    getStatus() {
        return {
            name: this.name,
            class: this.characterClass,
            level: this.level,
            health: `${this.health}/${this.maxHealth}`,
            mana: `${this.mana}/${this.maxMana}`,
            experience: this.experience,
            inventorySize: this.inventory.length
        };
    }
}

// ✅ Usage
const warrior = new Character("Budi", "Warrior");
warrior.addItem({ name: "Health Potion", type: "healing", value: 30 });
warrior.addItem({ name: "Mana Potion", type: "mana", value: 20 });

console.log(warrior.getStatus());
warrior.takeDamage(20);
warrior.useItem("Health Potion");
warrior.gainExperience(150);
console.log(warrior.getStatus());
```

## 📚 Referensi Belajar

### 🌐 Online Resources
- **MDN Web Docs**: [JavaScript Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
- **JavaScript.info**: [Objects](https://javascript.info/object)
- **W3Schools**: [JavaScript Objects](https://www.w3schools.com/js/js_objects.asp)

### 📖 Buku Rekomendasi
- "Eloquent JavaScript" by Marijn Haverbeke
- "JavaScript: The Definitive Guide" by David Flanagan
- "You Don't Know JS: this & Object Prototypes" by Kyle Simpson

### 🎥 Video Tutorial
- **Traversy Media**: JavaScript Objects Tutorial
- **The Net Ninja**: JavaScript Objects & Methods
- **Programming with Mosh**: JavaScript Objects

### 🛠️ Tools & Practice
- **CodePen**: Untuk eksperimen object
- **JSFiddle**: Untuk testing object methods
- **Replit**: Untuk project object
- **LeetCode**: Untuk latihan algoritma dengan object

## 🎯 Metode Belajar

### 📋 Step-by-Step Approach
1. **Start Simple**: Mulai dengan object sederhana
2. **Learn Methods**: Kuasai object methods satu per satu
3. **Practice Destructuring**: Latihan object destructuring
4. **Build Projects**: Aplikasikan dalam project nyata
5. **Master OOP**: Pelajari object-oriented programming

### 🔄 Learning Cycle
1. **Learn** → Baca teori dan konsep object
2. **Practice** → Tulis kode dan eksperimen
3. **Apply** → Gunakan dalam project nyata
4. **Review** → Evaluasi dan perbaiki
5. **Repeat** → Ulangi dengan konsep object baru

### 🎮 Interactive Learning
- **Codecademy**: Interactive JavaScript Objects
- **freeCodeCamp**: JavaScript Object Methods
- **Scrimba**: Object tutorials
- **JavaScript30**: Object-based challenges

## ⚠️ Common Pitfalls & Solutions

### 🚫 Error yang Sering Terjadi
```javascript
// ❌ Mengakses property yang tidak ada
let person = { name: "Budi" };
console.log(person.age);  // undefined

// ✅ Solusi: Gunakan optional chaining atau default value
console.log(person.age || "Age not set");
console.log(person?.age);

// ❌ Mutasi object yang tidak diinginkan
let original = { name: "Budi", age: 25 };
let copy = original;  // Reference, bukan copy
copy.age = 26;
console.log(original.age);  // 26 (original berubah)

// ✅ Solusi: Gunakan spread operator atau Object.assign
let safeCopy = { ...original };
let safeCopy2 = Object.assign({}, original);

// ❌ Arrow function dalam object method
let calculator = {
    value: 0,
    add: (num) => {
        this.value += num;  // ❌ this tidak merujuk ke object
    }
};

// ✅ Solusi: Gunakan regular function atau bind
let calculator2 = {
    value: 0,
    add(num) {
        this.value += num;
    }
};
```

### 🔧 Debugging Tips
```javascript
// ✅ Gunakan console.log untuk debugging object
let person = { name: "Budi", age: 25 };
console.log("Person object:", person);
console.log("Person keys:", Object.keys(person));
console.log("Person values:", Object.values(person));

// ✅ Gunakan console.table untuk object array
let users = [
    { name: "Budi", age: 25 },
    { name: "Ani", age: 30 }
];
console.table(users);

// ✅ Gunakan JSON.stringify untuk melihat struktur
console.log(JSON.stringify(person, null, 2));

// ✅ Debug object methods
let calculator = {
    value: 0,
    add(num) {
        console.log(`Adding ${num} to ${this.value}`);
        this.value += num;
        console.log(`Result: ${this.value}`);
        return this.value;
    }
};
```

## 🚀 Advanced Concepts (Preview)

### 🔄 Object Spread Operator
```javascript
// ✅ Spread operator untuk object
let person = { name: "Budi", age: 25 };
let updatedPerson = { ...person, age: 26 };

// ✅ Spread dengan multiple objects
let defaults = { theme: "light", language: "en" };
let userPrefs = { theme: "dark" };
let config = { ...defaults, ...userPrefs };

// ✅ Spread dengan nested objects
let user = {
    name: "Budi",
    profile: { age: 25, city: "Jakarta" }
};
let updatedUser = {
    ...user,
    profile: { ...user.profile, age: 26 }
};
```

### 🔄 Object Proxy
```javascript
// ✅ Proxy untuk intercepting object operations
let target = { name: "Budi", age: 25 };
let proxy = new Proxy(target, {
    get(obj, prop) {
        console.log(`Accessing property: ${prop}`);
        return obj[prop];
    },
    
    set(obj, prop, value) {
        console.log(`Setting property: ${prop} = ${value}`);
        obj[prop] = value;
        return true;
    }
});

proxy.name;  // "Accessing property: name"
proxy.age = 26;  // "Setting property: age = 26"
```

### 🔄 Object Symbols
```javascript
// ✅ Symbol untuk private properties
const _privateData = Symbol('privateData');

let obj = {
    [_privateData]: "This is private",
    publicData: "This is public"
};

console.log(obj.publicData);  // "This is public"
console.log(obj[_privateData]);  // "This is private"
```

---

> **💡 Pro Tip**: Object adalah struktur data paling fleksibel dalam JavaScript. Kuasai object untuk membuat kode yang lebih terorganisir dan maintainable! 