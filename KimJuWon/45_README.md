## 🔎 문제 코드

(45) What does this return?

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

A | "two"

## 🧠 관련 개념

### Promise.race() 메서드

- Promise.race() 메서드는 여러 개의 프로미스 중 가장 먼저 완료된 프로미스를 반환합니다.
- 가장 먼저 이행(fulfilled)되거나 거부(rejected)된 프로미스의 결과를 전달합니다.
- 여러 프로미스 중 하나라도 완료되면 그 결과를 즉시 반환하고 나머지 프로미스의 상태는 신경 쓰지 않습니다.
