## 🔎 문제 코드

What's the output?

```js
const { firstName: myName } = { firstName: "Lydia" };

console.log(firstName);
```

## ✅ 해설

D | ReferenceError

```jsx
const { firstName: myName } = { firstName: "Lydia" };
const myName = { firstName: "Lydia" }.firstName; // 위와 같은 코드

console.log(firstName); // ReferenceError
```

- firstName의 프로퍼티 값을 myName 변수에 할당합니다
- 그러나 firstName이라는 변수를 선언하지 않았기 때문에 ReferenceError가 발생합니다
- firstName의 값을 myName 변수에 할당했기 때문에 firstName에는 직접 접근할 수 없음
- 아래와 같이 firstName 변수를 만들어야합니다

```jsx
const { firstName } = { firstName: "Lydia" };
console.log(firstName); // Lydia
```

> 참고 `const myName = "Lydia";`와의 차이
>
> ```jsx
> // 구조 분해 할당: 객체 안의 데이터를 한꺼번에 추출할때 유리
> const person = { firstName: "Lydia", age: 28 };
> const { firstName: myName, age } = person;
>
> console.log(myName); // Lydia
> console.log(age); // 28
>
> // 직접 할당
> const myName = "Lydia";
> const age = 28;
>
> console.log(myName); // Lydia
> console.log(age); // 28
> ```

## 🧠 관련 개념

### 1. 객체의 구조 분해 할당

```jsx
// 객체의 key 값을 추출하여 동일한 이름의 변수로 할당합니다
const { key } = object;

// newName이라는 변수를 만든 후에 Key값에 할당합니다.
const { key: newName } = object;
```
