## 🔎 문제 코드

```js
const myPromise = Promise.resolve(Promise.resolve("Promise"));

function funcOne() {
  setTimeout(() => console.log("Timeout 1!"), 0);
  myPromise.then((res) => res).then((res) => console.log(`${res} 1!`));
  console.log("Last line 1!");
}

async function funcTwo() {
  const res = await myPromise;
  console.log(`${res} 2!`);
  setTimeout(() => console.log("Timeout 2!"), 0);
  console.log("Last line 2!");
}

funcOne();
funcTwo();
```

## ✅ 해설

```js
// 중첩 프로미스 생성
const myPromise = Promise.resolve(Promise.resolve("Promise"));
```

```js
function funcOne() {
  setTimeout(() => console.log("Timeout 1!"), 0); // (5) 매크로태스크로 큐에 들어감
  myPromise
    .then((res) => res) // (2) 첫 번째 then: res는 내부 Promise
    .then((res) => console.log(`${res} 1!`)); // (4) 두 번째 then: res는 "Promise"
  console.log("Last line 1!"); // (1) 동기 실행
}
```

```js
async function funcTwo() {
  const res = await myPromise; // (3) await Promise<Promise<string>> → await 후 "Promise"
  console.log(`${res} 2!`); // (4)
  setTimeout(() => console.log("Timeout 2!"), 0); // (6)
  console.log("Last line 2!"); // (5)
}
```

```bash
Last line 1! # 동기 코드
Promise 2! # 마이크로 태스크
Last line 2! # 마이크로 태스크
Promise 1! # 마이크로 태스크
Timeout 1! # 매크로 태스크
Timeout 2! # 매크로 태스크
```

## 🧠 관련 개념

### 중첩 Promise

`Promise.resolve(Promise.resolve("x"))` 형태는 자동으로 한 번 더 resolve 처리되기 때문에 await Promise.resolve(Promise.resolve("x")) -> "x" 까지 기다림.
