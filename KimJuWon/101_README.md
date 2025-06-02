## 🔎 문제 코드

```js
const one = false || {} || null;
const two = null || false || "";
const three = [] || 0 || true;

console.log(one, two, three);
```

## ✅ 해설

### const one = false || {} || null;

- false → falsy 값
- {} → 빈 객체지만 truthy 값 (첫 번째 truthy 값)
- null → 평가되지 않습니다 (단축 평가)

첫번째 truthy 값 {}이 반환됩니다

### const two = null || false || "";

- null → falsy 값
- false → falsy 값
- '' → falsy 값 (빈 문자열)

모든 값이 falsy이므로 마지막 값이 반환됩니다

### const three = [] || 0 || true;

- [] → 빈 배열이지만 truthy 값 (첫 번째 truthy 값)
- 0, true → 평가되지 않습니다 (단축 평가)

첫번째 truthy 값 []이 반환됩니다

## 🧠 관련 개념
