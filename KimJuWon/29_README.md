## 🔎 문제 코드

What's the output?

```js
const a = {};
const b = { key: "b" };
const c = { key: "c" };

a[b] = 123;
a[c] = 456;

console.log(a[b]);
```

A | 123
B | 456
C | undefined
D | ReferenceError

## ✅ 해설

B | 456

- 객체를 키로 사용하면, JavaScript는 이를 문자열로 변환합니다.
- b와 c는 객체이므로 **"[object Object]"**로 변환됩니다.
- 즉, 아래와 같은 코드와 동일하게 동작합니다.

```js
a["[object Object]"] = 123;
a["[object Object]"] = 456;
```

- 따라서 마지막으로 할당된 값인 456이 출력됩니다.

## 🧠 관련 개념

### 객체 키로 객체 사용 시

- 객체를 키로 사용하면 내부적으로 문자열로 변환됩니다.
- 대부분의 객체를 문자열로 변환하면 **"[object Object]"**가 됩니다.
- 여러 객체를 키로 사용하려면, Map 객체를 사용하여 참조 자체를 키로 사용해야 합니다.
- Map 객체는 객체를 직접 키로 사용할 수 있으므로 이러한 문제를 방지할 수 있습니다.

```js
const a = new Map();
const b = { key: "b" };
const c = { key: "c" };

a.set(b, 123);
a.set(c, 456);

console.log(a.get(b)); // 123
console.log(a.get(c)); // 456
```
