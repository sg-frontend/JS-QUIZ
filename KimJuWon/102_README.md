## 🔎 문제 코드

What's the value of output?

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

### firstFunction()

- myPromise().then(res => console.log(res)): Promise는 즉시 resolve되지만, then 콜백은 마이크로태스크 큐에 들어감
- console.log('second'): 즉시 실행 → "second" 출력

### secondFunction()

- await myPromise(): 함수 실행이 일시 중단되고 Promise가 resolve될 때까지 대기
- Promise가 resolve되면 → "I have resolved!" 출력
- console.log('second'): 다음 줄 실행 → "second" 출력

## 🧠 관련 개념

### Promise.then()과 async/await의 차이점

1. Promise.then()

- 비차단 (Non blocking)
- 즉시 다음 코드로 진행합니다
- Promise 결과는 마이크로테스트 큐에서 처리합니다
- 현재 실행 컨텍스트를 차단하지 않습니다

2. async/await

- await 지점에서 함수 실행을 일시 중단합니다
- Promise가 resolve될때까지 기다립니다
- 순차적인 실행으로 코드 흐름이 직관적입니다
