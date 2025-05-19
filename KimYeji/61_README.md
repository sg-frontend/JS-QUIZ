## 🔎 문제 코드

```js
const person = { name: "Lydia" };

Object.defineProperty(person, "age", { value: 21 });

console.log(person);
console.log(Object.keys(person));
```

## ✅ 해설

````js
const person = { name: 'Lydia' };
// person 객체에 name 속성 추가

Object.defineProperty(person, 'age', { value: 21 });
// age 속성 추가

console.log(person); //  { name: 'Lydia', age: 21 }

console.log(Object.keys(person)); // ['name']
// Object.keys는 열거 가능한 속성만 반환함. age는 enumerable이 false이기 때문에 포함 X
```

## 🧠 관련 개념

### `Object.defineProperty()`

객체에 새로운 속성을 정의하거나 기존 속성을 수정할 때 사용함.

- enumerable : false (기본값)
- configurable: false (기본값)
- writable: false (기본값)

### `Object.keys()`

객체의 열거 가능한 속성 이름들을 배열로 반환함. 열거 가능하지 않은 속성은 반환하지 않음.
````
