## 🔎 문제 코드

```js
[1, 2, 3, 4].reduce((x, y) => console.log(x, y));
```

## ✅ 해설

첫 번째 반복 : x = 1, y = 2 -> console.log(1,2) 실행 -> undefined 반환
두 번째 반복 : x = undefined, y = 3 -> console.log(undefined, 3) -> undefined 반환
세 번째 반복 : x = undefined, y = 4 -> console.log(undefined, 4) -> undefined 반환

## 🧠 관련 개념

### `Array.reduce()`

배열의 모든 요소를 돌면서 하나의 값으로 줄임

```js
array.reduce(callback, [, initialValue]);
```

- accumulator (x): 이전 콜백의 반환값
- currentValue (y): 현재 처리 중인 요소
- currentIndex (선택)
- array (선택)
