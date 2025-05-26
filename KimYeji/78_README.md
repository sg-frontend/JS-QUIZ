## 🔎 문제 코드

```js
const add = () => {
  const cache = {};
  return (num) => {
    if (num in cache) {
      return `From cache! ${cache[num]}`;
    } else {
      const result = num + 10;
      cache[num] = result;
      return `Calculated! ${result}`;
    }
  };
};

const addFunction = add();
console.log(addFunction(10));
console.log(addFunction(10));
console.log(addFunction(5 * 2));
```

## ✅ 해설

```js
const add = () => {
  const cache = {};
  return (num) => {
    if (num in cache) {
      return `From cache! ${cache[num]}`;
    } else {
      const result = num + 10;
      cache[num] = result;
      return `Calculated! ${result}`;
    }
  };
};

const addFunction = add();
console.log(addFunction(10));
// cache = {}
// result = 10 + 10 = 20
// cache[10] = 20

console.log(addFunction(10));
// cache = { 10: 20 }
// 10이 캐시에 있음 -> From cache: 20 반환

console.log(addFunction(5 * 2));
// 5 * 2 = 10
// cache = { 10: 20 }
// 10이 캐시에 있음 -> From cache: 20 반환
```
