## 🔎 문제 코드

```js
function sayHi() {
  console.log(name);
  console.log(age);
  var name = "Lydia";
  let age = 21;
}

sayHi();
```

## ✅ 해설

### 1. var / let 차이

- `var name`은 호이스팅 되며, 선언 시점 코드 이전의 초기값은 undefined임.
- `let age`는 호이스팅 되지만, 초기화는 실제 코드가 실행되는 시점에 이루어짐(TDZ).

### 2. 실행 결과

```js
//  호이스팅 + 초기값 undefined
console.log(name); // undefined

//  호이스팅 + TDZ
console.log(age); // ReferenceError
```

## 🧠 관련 개념

### 호이스팅

변수와 함수 선언이 코드 실행 전에 scope의 최상단으로 끌어 올려지는 자바스크립트 작동 방식임.

**함수 선언**은 전체가 호이스팅 되기 때문에 함수 호출이 먼저 오더라도 에러 없이 실행 가능함.

**변수 선언**은 호이스팅 되지만 var <-> let/const의 초기화 시점이 다름.

`var` 변수는 함수 스코프를 가지며, 선언만 위로 올라가고 초기화는 작성한 코드자리에 있기 때문에 초기화 전에 값을 사용하려 하면 undefined 에러가 발생함.

`let/const` 블록 스코프를 가지며, 변수는 호이스팅 되지만 초기화 되지 않은 상태(TDZ) 에 있기 때문에 접근할 수 없고 ReferenceError가 발생함.
