# কেন `any` কে "type safety hole" বলা হয়? আর কেন `unknown` বেশি safe?

## ভূমিকা

TypeScript-এর মূল শক্তি হলো **type safety** — অর্থাৎ compile time-এ ভুল ধরা। কিন্তু `any` এই সিস্টেমকে ভেঙে দেয়। বড় project-এ `any` ব্যবহার করলে runtime-এ crash আসে, যেটা আগে থেকে ধরার কোনো উপায় থাকে না।

---

## `any` — Type System-এর ফাঁকফোকর

`any` ব্যবহার করলে TypeScript essentially বলে:

> **"তুমি যা করো করো, আমি কিছু check করবো না।"**

```typescript
let data: any = "hello";

data.toUpperCase(); // ok
data(); // runtime crash করবে — কিন্তু TS কোনো warning দেয়নি!
```

এজন্যই `any` কে বলা হয় **"Type Safety Hole"** — কারণ এটা type system কে সম্পূর্ণভাবে bypass করে। TypeScript যে কারণে ব্যবহার করা হচ্ছে, `any` সেই উদ্দেশ্যটাই নষ্ট করে দেয়।

---

## `unknown` — `any`-এর Safer Version

`unknown` হলো `any`-এর নিরাপদ বিকল্প।

### উদাহরণ

```typescript
let data: unknown = "hello";

data.toUpperCase(); //  Error: Object is of type 'unknown'
```

`unknown` সরাসরি ব্যবহার করতে দেয় না। আগে **type narrow** করতে হবে:

```typescript
if (typeof data === "string") {
  data.toUpperCase(); // ✅ safe
}
```

---

## Type Narrowing কী?

**Type narrowing** মানে হলো, যেকোনো broad type কে runtime check-এর মাধ্যমে একটি specific type-এ নিয়ে আসা।

```typescript
function printLength(value: unknown) {
  if (typeof value === "string") {
    console.log(value.length); // এখানে TypeScript জানে value একটা string
  }
}
```

এখানে যা হচ্ছে ধাপে ধাপে:

- প্রথমে `value` এর type ছিল `unknown`
- `typeof value === "string"` check করার পর TypeScript বুঝে নেয় এটা `string`
- তারপর `string`-এর সব method নিরাপদে ব্যবহার করা যাচ্ছে

এই process-টাকেই বলে **type narrowing**।

---

## উপসংহার

- `any` ব্যবহার মানে **blind coding**
- `unknown` ব্যবহার মানে **controlled coding**
- বড় project-এ `any` avoid করাই **best practice**
