## 🔎 문제 코드

```js
// What's the output?
function sayHi() {
  console.log(name);
  console.log(age);
  var name = "Lydia";
  let age = 21;
}

sayHi();
```

## ✅ 해설

- var로 선언된 변수는 호이스팅이 되어 초기값이 undefined로 설정됩니다
- let으로 선언된 변수는 호이스팅되지만 TDZ(일시적 사각지대)에 있기 때문에 선언 전에 접근하면 ReferenceError가 발생합니다

## 🧠 관련 개념

### 1. 호이스팅

: 함수 안에 있는 선언들을 모두 끌어 올려서 해당 함수 유효 스코프의 최상단에 선언하는 것입니다.

#### 1.1 호이스팅 대상

자바스크립트는 ES6에서 도입된 let,const를 포함하여 모든 선언(var, let, const, function, function\*, class)을 호이스팅합니다.

#### 1.2 함수 호이스팅

- 함수 선언문의 호이스팅
  : 함수 선언문은 코드를 구현한 위치와 관계없이 자바스크립트의 특징인 호이스팅에 따라 브라우저가 자바스크립트를 해석 할 때 맨위로 끌어 올려집니다.

- 함수 표현식의 호이스팅
  : 함수 표현식은 함수 선언문과 달리 선언과 호출 순서에 따라서 정상적으로 함수가 실행되지 않을 수 있습니다.

> “[함수이름] is not defined” 이라고 오류가 나오지 않고, “[함수이름] is not a function”이라는 TypeError가 나오는 이유?
>
> printName이 실행되는 순간 (Hoisting에 의해) inner는 ‘undefined’으로 지정되기 때문
> inner가 undefined라는 것은 즉, 아직은 함수로 인식이 되지 않고 있다는 것을 의미합니다. 그렇다면 왜 undefined가 될까요?

### 2. Temporal Dead Zone(TDZ)

: 선언 전에 변수를 사용하는 것일 비허용하는 개념상의 공간입니다

#### 2.1 const let var

- const

  ```js
  white; // throws `ReferenceError`
  const white = "#FFFFFF";
  white; // => '#FFFFFF'
  ```

- let

  ```js
  white; // throws `ReferenceError`
  let white = "#FFFFFF";
  white; // => '#FFFFFF'
  ```

- var
  ```js
  white; // => undefined
  var white = "#FFFFFF";
  white; // => '#FFFFFF'
  ```
