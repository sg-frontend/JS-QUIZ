## 🔎 문제 코드

What's the output?

```js
function sayHi() {
  return (() => 0)();
}

console.log(typeof sayHi());
```

## ✅ 해설

B | "number"

- 즉시 실행 함수(IIFE)를 이용하여 숫자 0을 바로 반환합니다.
- typeof는 해당 값의 타입을 문자열로 반환합니다
- typeof 0의 결과는 "number"이므로 출력도 "number"입니다.

## 🧠 관련 개념
