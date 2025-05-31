## 🔎 문제 코드

```js
const person = {
  name: "Lydia",
  age: 21,
};

const changeAge = (x = { ...person }) => (x.age += 1);
const changeAgeAndName = (x = { ...person }) => {
  x.age += 1;
  x.name = "Sarah";
};

changeAge(person);
changeAgeAndName();

console.log(person);
```

## ✅ 해설

```js
const person = {
  name: "Lydia",
  age: 21,
};

// 인자를 전달 받지 않으면 얕은 복사를 하여 default 값으로 사용함
const changeAge = (x = { ...person }) => (x.age += 1);

const changeAgeAndName = (x = { ...person }) => {
  x.age += 1;
  x.name = "Sarah";
};

changeAge(person); // person 객체를 전달하였기 때문에 person 원본 사용
changeAgeAndName(); // 인자를 전달하지 않았기 때문에 얕은 복사본 사용

console.log(person);
```

## 🧠 관련 개념

### default parameter

함수 파라미터에 기본 값을 설정하여 아무 값도 전달하지 않은 경우에 디폴트 값을 사용할 수 있음.

### 얕은 복사

`{..obj}` : 객체의 최상위 프로퍼티만 복사되고, 새 객체로 생성되기 때문에 원본 객체와는 별개로 인식함.
