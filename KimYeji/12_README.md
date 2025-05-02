## 🔎 문제 코드

```js
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const lydia = new Person("Lydia", "Hallie");
const sarah = Person("Sarah", "Smith");

console.log(lydia);
console.log(sarah);
```

## ✅ 해설

### 1. `new` 키워드

`new` 키워드는 생성자 함수로 객체를 생성할 때 사용하고, 해당 객체가 생성될 때 자동으로 this를 해당 객체로 바인딩함.

`const lydia = new Person("Lydia", "Hallie");` 는 new 를 사용하여 객체를 생성하였기 때문에 Person 생성자 함수에서 this로 가리켜짐.

`const sarah = Person("Sarah", "Smith");` 는 new 키워드를 사용하지 않았기 때문에 this가 전역 객체를 참조하여 전역 객체에 속성들이 추가 됨. new 없이 함수를 호출하는 경우에 Person 함수는 아무 값도 반환하지 않아 undefined를 출력함.

### 2. 실행 결과

```js
console.log(lydia); // Person { firstName: "Lydia", lastName: "Hallie" }
console.log(sarah); // undefined
```

## 🧠 관련 개념

### `new`

new 키워드는 객체 생성을 위해 생성자 함수를 호출할 때 사용함.

- new 키워드를 사용하면

  1. 빈 객체 생성
  2. this가 새로 생성된 해당 객체를 가리킴
  3. 생성자 함수 내에서 this에 속성이나 메서드를 할당할 수 있음
  4. 생성된 객체가 new 표현식 결과로 반환됨

- new 없이 호출하면

  1. this는 전역 객체 참조 (전역 스코프에 속성 추가되는 문제)
  2. 실행 컨텍스트에 따라 동적으로 결정

- new 없이 반환값 처리
  1. 명시적으로 반환값을 설정하지 않으면 생성자 함수가 undefined 반환
