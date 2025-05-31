## 🔎 문제 코드

```js
async function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield Promise.resolve(i);
  }
}

(async () => {
  const gen = range(1, 3);
  for await (const item of gen) {
    console.log(item);
  }
})();
```

## ✅ 해설

```js
// 비동기 제너레이터 함수 (Promise를 반환하는 값도 yield할 수 있음.)
async function* range(start, end) {
  for (let i = start; i <= end; i++) {
    yield Promise.resolve(i); // 1,2,3 값에 대해 resolve(i)를 yield 함
  }
}

// 즉시 실행 함수로 감싸서 await를 사용할 수 있게 만들었음.
(async () => {
  const gen = range(1, 3); // async generator 객체를 만듦.
  for await (const item of gen) {
    console.log(item);
  }
})();
```

```bash
	1.	gen.next() → Promise.resolve(1) 반환됨
	2.	await 해서 1 출력
	3.	gen.next() → Promise.resolve(2)
	4.	await 해서 2 출력
	5.	gen.next() → Promise.resolve(3)
	6.	await 해서 3 출력
```

## 🧠 관련 개념

### async function\* range(start, end)

async generator 함수이고, yield 키워드를 통해 Promise를 반환하더라도 For await ...of 문을 사용하여 순차적으로 처리할 수 있음.

### for await... of

Symbol.asyncIterator가 구현된 iterable에서 사용 가능하고, 각 반복마다 await로 값을 기다림.
