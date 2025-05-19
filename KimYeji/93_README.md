## 🔎 문제 코드

```js
const person = {
  name: "Lydia",
  age: 21,
};

for (const [x, y] of Object.entries(person)) {
  console.log(x, y);
}
```

## ✅ 해설

```js
Object.entries(person);
// [
//   ["name", "Lydia"],
//   ["age", 21]
// ]
```

```js
[x, y] = ["name", "Lydia"][
  // x = "name", y = "Lydia"

  (x, y)
] = ["age", 21];
// x = "age", y = 21
```

## 🧠 관련 개념

### `Object.entries()`

객체의 키-값 쌍을 배열로 반환함. 각 요소는 [key, value] 형태의 배열임. 열거 가능한 속성만 포함하고 있음.
