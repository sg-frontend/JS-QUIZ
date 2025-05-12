## 🔎 문제 코드

```js
const firstPromise = new Promise((res, rej) => {
  setTimeout(res, 500, "one");
});

const secondPromise = new Promise((res, rej) => {
  setTimeout(res, 100, "two");
});

Promise.race([firstPromise, secondPromise]).then((res) => console.log(res));
```

## ✅ 해설

```js
const firstPromise = new Promise((res) => {
  setTimeout(res, 500, "one"); // 500ms 후 'one'
});

// 2. 100ms 이기 때문에 먼저 처리되는 promise
const secondPromise = new Promise((res) => {
  setTimeout(res, 100, "two"); // 100ms 후 'two'
});

// 2개의 프로미스 중에 먼저 처리되는 하나만 사용
Promise.race([firstPromise, secondPromise]).then((res) => console.log(res));
```

## 🧠 관련 개념

### `Promise.race`

`Promise.race()`는 배열로 전달된 프로미스 중에서 가장 먼저 resolve되거나 reject 되는 프로미스의 결과를 반환함.

여러 비동기 작업 중에서 가장 빠른 응답 하나만 필요할 때 사용하고, 이후 완료된 다른 프로미스는 무시됨. (비동기적으로 실행되지만 결과로 반영되지는 않음.)

### `setTimeout(callback, delay, value)`

value는 지정 시간 이후 callback에 전달됨.
