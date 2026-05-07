# Assignment: Problem Solving with TypeScript & OOP

## Overview

This assignment demonstrates fundamental TypeScript concepts including data typing, interfaces, class-based inheritance, type guards, generics, and data structure manipulation. All solutions follow clean code principles with no unnecessary comments or console statements.

---

## Solutions

All 7 problems are solved in a single file: `solutions.ts`

### Problem 1 — Filter Even Numbers

**Concept:** Array filtering with explicit TypeScript typing.

**Function:** `filterEvenNumbers(numbers: number[]): number[]`

```
Input:  [1, 2, 3, 4, 5, 6]
Output: [2, 4, 6]
```

---

### Problem 2 — Reverse a String

**Concept:** String manipulation using built-in array methods.

**Function:** `reverseString(str: string): string`

```
Input:  "typescript"
Output: "tpircsepyt"
```

---

### Problem 3 — Type Checking with Union Types

**Concept:** Union types and type guards with literal return types.

**Type:** `StringOrNumber = string | number`

**Function:** `checkType(value: StringOrNumber): string`

```
Input:  "Hello"  →  Output: "String"
Input:  42       →  Output: "Number"
```

---

### Problem 4 — Generic Property Accessor

**Concept:** Generics with `keyof` constraints for type-safe object property access.

**Function:** `getProperty<T, K extends keyof T>(obj: T, key: K): T[K]`

```
Input:  { id: 1, name: "John Doe", age: 21 }, "name"
Output: "John Doe"
```

---

### Problem 5 — Toggle Read Status

**Concept:** Interface extension and immutable object transformation.

**Interfaces:**

- `Book` — base interface with `title`, `author`, `publishedYear`
- `BookWithReadStatus extends Book` — adds `isRead: boolean`

**Function:** `toggleReadStatus(data: Book): BookWithReadStatus`

```
Input:  { title: "TypeScript Guide", author: "Jane Doe", publishedYear: 2024 }
Output: { title: "TypeScript Guide", author: "Jane Doe", publishedYear: 2024, isRead: true }
```

---

### Problem 6 — Class Inheritance

**Concept:** OOP with class inheritance, constructor chaining via `super()`, and access modifiers.

**Classes:**

- `Person` — base class with `name` and `age` using TypeScript shorthand constructor (`public`)
- `Student extends Person` — adds `grade` property and a `getDetails()` method

**Function:** `student.getDetails(): string`

```
Input:  new Student("Alice", 20, "A")
Output: "Name: Alice, Age: 20, Grade: A"
```

---

### Problem 7 — Array Intersection

**Concept:** Functional array manipulation using `reduce` and `includes`.

**Function:** `getIntersection(arr1: number[], arr2: number[]): number[]`

```
Input:  [1, 2, 3, 4, 5], [3, 4, 5, 6, 7]
Output: [3, 4, 5]
```

## File Structure

```
.
└── solutions.ts
```

## How to Run

```bash
# Compile
npx tsc solutions.ts

# Run
node solutions.js

# Or run directly with ts-node
npx ts-node solutions.ts
```
