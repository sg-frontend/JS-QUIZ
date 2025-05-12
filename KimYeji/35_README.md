## 🔎 문제 코드

```js
// falsy 값 찾기
0;
new Number(0);
("");
(" ");
new Boolean(false);
undefined;
```

## ✅ 해설

### 1. JS에서 falsy 값

자바스크립트의 불리언 값으로 평가될 때 false로 변환되는 값들이 falsy 값임.

1. `undefined`
2. `null`
3. `NaN`
4. `false`
5. `''`
6. `0`
7. `-0`
8. `0n (BigInt(0))`

### 2. 실행 결과

```js
0; // falsy
new Number(0); // truthy
(""); // falsy
(" "); // truthy
new Boolean(false); // truthy
undefined; // falsy
```
