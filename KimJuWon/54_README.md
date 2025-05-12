## 🔎 문제 코드

What's the output?

```js
(() => {
  let x = (y = 10);
})();

console.log(typeof x);
console.log(typeof y);
```

A | "undefined", "number"

## ✅ 해설

- y = 10이므로 number
  - 선언이 된 것이 아니므로 전역변수로 간주됩니다.
  - 브라우저 환경: window.y = 10 or Node.js 환경: global.y = 10
- x는 y의 값을 받아 x = 10이 됩니다

  - 그러나 x는 let 키워드로 선언되어 블록 스코프를 가지므로 함수 안에서만 유효하게 됩니다

- 따라서 즉시 실행함수 밖에서는 x는 블록 범위 변수라 접근이 불가능하고, y는 전역 변수로 함수밖에서도 접근 가능합니다

## 🧠 관련 개념
