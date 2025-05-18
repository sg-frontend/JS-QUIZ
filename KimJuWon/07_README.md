## 🔎 문제 코드

```js
let a = 3;
let b = new Number(3);
let c = 3;

console.log(a == b);
console.log(a === b);
console.log(b === c);
```

## ✅ 해설

```
let b = new Number(3);
```

위의 코드는 객체형이므로 엄격한 비교를 할 경우 number !== object가 되어 a===b와 a===c는 false입니다

## 🧠 관련 개념
