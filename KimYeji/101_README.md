## 🔎 문제 코드

```js
const one = false || {} || null;
const two = null || false || "";
const three = [] || 0 || true;

console.log(one, two, three);
```

## ✅ 해설

```js
const one = false || {} || null;
// false (falsy) || {} (truthy) -> 반환

const two = null || false || "";
// null (falsy) || false (falsy) || '' (falsy) -> 반환

const three = [] || 0 || true;
// [] (truthy) -> 반환

console.log(one, two, three);
// {} "" []
```

## 🧠 관련 개념

### || (OR 연산자)

첫 번째 truthy 값을 반환함. (truthy : Boolean으로 변환했을 때 true가 되는 값)
falsy 값 : false, 0, NaN, "", null, undefined
