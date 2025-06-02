## 🔎 문제 코드

```js
const animals = {};
let dog = { emoji: "🐶" };
let cat = { emoji: "🐈" };

animals[dog] = { ...dog, name: "Mara" };
animals[cat] = { ...cat, name: "Sara" };

console.log(animals[dog]);
```

## ✅ 해설

B | { emoji: "🐈", name: "Sara" }

1. animals[dog] = { ...dog, name: "Mara" }

- dog 객체가 키로 사용되면서 "[object Object]" 문자열로 변환합니다
- 실제로는 animals["[object Object]"] = { emoji: '🐶', name: "Mara" }

2. animals[cat] = { ...cat, name: "Sara" }

- cat 객체도 키로 사용되면서 "[object Object]" 문자열로 변환합니다
- 실제로는 animals["[object Object]"] = { emoji: '🐈', name: "Sara" }
- 이전 값을 덮어씁니다

3. console.log(animals[dog])

- dog 객체가 다시 "[object Object]"로 변환합니다
- animals["[object Object]"]를 조회합니다

=> { emoji: '🐈', name: "Sara" } (cat의 값)

## 🧠 관련 개념
