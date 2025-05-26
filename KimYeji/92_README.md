## 🔎 문제 코드

```js
function giveLydiaPizza() {
  return "Here is pizza!";
}

const giveLydiaChocolate = () =>
  "Here's chocolate... now go hit the gym already.";

console.log(giveLydiaPizza.prototype);
console.log(giveLydiaChocolate.prototype);
```

## ✅ 해설

```js
function giveLydiaPizza() {
  return "Here is pizza!";
}

const giveLydiaChocolate = () =>
  "Here's chocolate... now go hit the gym already.";

console.log(giveLydiaPizza.prototype);
// { constructor: ƒ } - 자체 Prototype 가짐

console.log(giveLydiaChocolate.prototype);
//  undefined - 화살표 함수는 prototype이 없음
```

## 🧠 관련 개념

### 일반 함수 / 화살표 함수

- **일반 함수**

  - function 키워드
  - 자체 prototype 객체를 가짐
  - 생성자 함수로 사용 가능

- **화살표 함수**
  - => 문법 선언
  - prototype 속성 없음
  - 생성자 함수로 사용 불가
