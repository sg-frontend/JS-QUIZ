## 🔎 문제 코드

```js
const name = "Lydia Hallie";
console.log(name.padStart(13));
console.log(name.padStart(2));
```

## ✅ 해설

```js
const name = "Lydia Hallie";
console.log(name.padStart(13)); // 앞에 공백 1개 추가
console.log(name.padStart(2)); // 그대로 출력
```

## 🧠 관련 개념

### `String.padStart()`

```js
str.padStart(targetLegth[, padString])
```

문자열의 시작 부분을 다른 문자열로 채움.

- targetLength: 목표 문자열 길이
- padString: 채울 문자열 (기본값: 공백)
