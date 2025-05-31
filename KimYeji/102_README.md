## 🔎 문제 코드

```js
const myPromise = () => Promise.resolve("I have resolved!");

function firstFunction() {
  myPromise().then((res) => console.log(res));
  console.log("second");
}

async function secondFunction() {
  console.log(await myPromise());
  console.log("second");
}

firstFunction();
secondFunction();
```

## ✅ 해설

```js
const myPromise = () => Promise.resolve("I have resolved!");

function firstFunction() {
  myPromise().then((res) => console.log(res)); // 1-1. 마이크로태스크 큐에 console 등록
  console.log("second"); // 1-2. 즉시 실행
}

async function secondFunction() {
  console.log(await myPromise()); // 2-1. Promise.resolve 호출 후 마이크로태스크에 등록
  console.log("second");
}

firstFunction(); // 1. 호출
secondFunction(); // 2. 호출
```

```bash
second, I have resolved!

I have resolved!, second
```

## 🧠 관련 개념

### Promise.then()

Promise 는 JS의 비동기 처리 객체임. then() 메서드를 호출하면 해당 콜백은 마이크로태스크 큐(현재 동기 코드 실행이 완료되고 즉시 처리되는 큐)에 등록됨.

### await

await는 Promise가 resolve될 때까지 기다리는 키워드임. 실제로 Promise.then() 을 사용하는 것과 유사하게 동작하고, 다음 줄의 실행을 중단한 다음에 해당 Promise가 resolve되면 이후 코드를 마이크로태스크 큐에 등록함.

### 이벤트 루프, 큐

- 콜 스택

  - 동기 코드에 실행
  - console.log()

- 마이크로태스크 큐

  - 콜스택이 비어있는 시점에 우선 실행
  - Promise.then, await

- 태스크 큐
  - 마이크로태스크 큐 처리 후에 실행
  - setTimeout, setInterval
