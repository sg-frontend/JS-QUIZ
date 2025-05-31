## 🔎 문제 코드

```js
const promise1 = Promise.resolve("First");
const promise2 = Promise.resolve("Second");
const promise3 = Promise.reject("Third");
const promise4 = Promise.resolve("Fourth");

const runPromises = async () => {
  const res1 = await Promise.all([promise1, promise2]);
  const res2 = await Promise.all([promise3, promise4]);
  return [res1, res2];
};

runPromises()
  .then((res) => console.log(res))
  .catch((err) => console.log(err));
```

## ✅ 해설

```js
const promise1 = Promise.resolve("First"); // 성공
const promise2 = Promise.resolve("Second"); // 성공
const promise3 = Promise.reject("Third"); // 실패
const promise4 = Promise.resolve("Fourth"); // 성공
```

```js
const runPromises = async () => {
  const res1 = await Promise.all([promise1, promise2]); // 성공, 성공
  const res2 = await Promise.all([promise3, promise4]); // 실패, 성공  -> 전체 Reject
  return [res1, res2];
};
```

```js
runPromises()
  .then((res) => console.log(res))
  .catch((err) => console.log(err)); // 두번째 await에서 에러 발생
```

```bash
Third
```

## 🧠 관련 개념

### Promise.all([])

전달된 promise 중에 하나라도 Reject되면 전체가 reject 처리됨.
