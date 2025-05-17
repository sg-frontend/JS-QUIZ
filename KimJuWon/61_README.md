## 🔎 문제 코드

What's the output?

```js
const person = { name: "Lydia" };

Object.defineProperty(person, "age", { value: 21 });

console.log(person);
console.log(Object.keys(person));
```

## ✅ 해설

B | { name: "Lydia", age: 21 }, ["name"]

- Object.defineProperty로 속성을 추가하게 되면 enumerable: false의 설정을 가지게 됩니다
- Object.keys()는 enumerable한 값만 반환하기 때문에 age:21은 반환하지 않습니다

## 🧠 관련 개념

### 1. Object.defineProperty

- Object.defineProperty로 속성을 추가하면 아래의 설정들을 가집니다
  - writable: false (값을 수정할 수 없습니다)
  - enumerable: false (반복문이나 Object.keys에서 표시되지 않습니다)
  - configurable: false (속성을 삭제하거나 속성 설명자를 수정할 수 없습니다)

### 2. Object.keys

- Object.keys()는 열거 가능한(enumerable) 속성만 반환합니다
