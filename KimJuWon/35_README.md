## 🔎 문제 코드

Which of these values are falsy?

```js
0;
new Number(0);
("");
(" ");
new Boolean(false);
undefined;
```

## ✅ 해설

A | 0, "", undefined

- new Number(0)과 new Boolean(false)는 객체이므로 Truthy

## 🧠 관련 개념

### Truthy와 Falsy

#### Falsy

- undefined
- null
- NaN
- false
- '' (빈 문자열)
- 0
- -0
- 0n (BigInt의 0)
