## 🔎 문제 코드

```js
function* generator(i) {
  yield i;
  yield i * 2;
}

const gen = generator(10);

console.log(gen.next().value);
console.log(gen.next().value);
```

## ✅ 해설

1. generator 함수 (function\*)

function\* 키워드는 제너레이터 함수를 정의할 때 사용함. 제네레이터 함수는 실행 도중에 `yield` 키워드를 사용하여 일시 중단 할 수 있음. 호출하면 즉시 실행되지 않고 이터레이터 객체를 반환함. 이터레이터 .next() 를 호출해야 실제 실행 시작함.

```js
function* generator(i) {
  yield i; // next() 호출 → 10 반환하고 중단함
  yield i * 2; // 호출 → 20 반환하고 중단함
}

const gen = generator(10); // 제너레이터 객체 생성 (아직 실행 안 됨)

console.log(gen.next().value); // 10
console.log(gen.next().value); // 20
```

## 🧠 관련 개념

### `function\*``

제네레이터 함수 정의할 때 사용하는 키워드

### `yield`

값을 반환하여 실행을 일시 중단함. 이후 .next()를 호출하면 중단된 위치 다음 줄부터 다시 실행을 이어감.

### `next()`

다음 yield 까지 실행을 이어감. 반환 값은 { value, done } 형태의 객체임.
