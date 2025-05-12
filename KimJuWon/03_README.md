## 🔎 문제 코드

```js
const shape = {
  radius: 10,
  diameter() {
    return this.radius * 2;
  },
  perimeter: () => 2 * Math.PI * this.radius,
};

console.log(shape.diameter());
console.log(shape.perimeter());
```

## ✅ 해설

- diameter()는 일반 함수이므로 this가 shape를 가리켜 10 \* 2 = 20입니다.
- perimeter는 화살표 함수이며, this는 shape가 아니라 상위 스코프의 this를 가리켜 undefined.radius로 NaN입니다.

## 🧠 관련 개념

### 1. this 바인딩

: 자바스크립트에서 this가 참조하는 것은 함수가 호출되는 방식에 따라 결정됩니다

#### 1.1 기본 바인딩 (Default Binding)

- this는 전역 객체에 바인딩됩니다.
- 브라우저 환경의 경우 window, Node.js 환경인 경우는 global

```js
function test() {
  const a = 10;
  console.log(this.a);
}

test(); // undefined
```

- 위와 같은 경우에는 this는 전역 객체에 바인딩되고 전역객체에는 a라는 프로퍼티가 없기 때문에 undefined가 출력됩니다.
- 전역객체에 a라는 프로퍼티가 있는 경우 해당 a프로퍼티의 값을 출력하게 됩니다.

```js
window.a = 10;

function test() {
  console.log(this.a);
}

test(); // 10
```

- 엄격모드에서는 기본 바인딩 대상에서 전역객체는 제외됩니다

```js
window.a = 10;

function test() {
  console.log(this.a);
}

test(); // TypeError: Cannot read property 'a' of undefined
```

#### 1.2 암시적 바인딩

- 함수가 객체의 메서드로서 호출되는 상황에서 this가 바인딩되는 것을 말합니다
- this는 해당 함수를 호출한 객체 즉 콘텍스트 객체에 바인됭됩니다

```js
const test = {
  a: 20,
  bar: function () {
    console.log(this.a);
  },
};

test.bar(); // 20
setTimeout(test.bar, 1); // undefined
```

- 암시적 바인딩을 사용할 때 발생할 수 있는 문제는 위와 같은 상황에서 함수를 매개변수(콜백)로 넘겨서 실행하는 것입니다
- 위와 같이 객체에 정의되어있는 함수의 레퍼런스를 매개변수로 전달하는 상황에서 undefined가 나옵니다
- 이런 결과가 나오는 이유는 setTimeout함수 안에 전달한 콜백은 test라는 함수의 래퍼런스일뿐, test의 콘텍스트를 가지고 있지 않기 때문입니다. => 암시적 바인딩 소실
- 아래와 같이 호출되는 콜백은 test 객체의 콘텍스트에서 실행되는 것이 아니기 때문에 this는 기본 바인딩이 적용되어 전역 객체에 바인딩 됩니다.

```js
function setTimeout(cb, delay) {
  // delay 만큼 기다린다
  cb(); // 기본 바인딩, bar.test()가 아닌 test()와 같다
}
```

#### 1.3 명시적 바인딩

- 자바스크립트의 모든 Function 은 call(), apply(), bind()라는 프로토타입 메소드를 가지고 있습니다
- 이중 하나를 호출함으로써 this 바인딩을 코드에서 명시하는 것을 명시적 바인딩이라고 합니다
- 이때의 this는 명시한 객체에 바인딩됩니다.

```js
const test = {
  a: 20,
};

function bar() {
  console.log(this.a);
}

// Function 프로토타입 메서드 call, apply의 매개변수로 바인딩할 객체를 넘겨주면서 bar 함수를 실행할 때의 this 컨텍스트를 test로 직접 바인딩
// call과 apply의 동작은 같지만 두번째 매개변수로 객체의 인자를 전달해주는데(e.g. 생성자의 매개변수), call은 매개변수의 목록, apply는 배열을 받는다는 차이
bar.call(test); // 20
bar.apply(test); // 20

// 하드 바인딩
// bind 메서드는 매개변수로 전달받은 오브젝트로 this가 바인딩된 함수를 반환
// 하드 바인딩된 함수는 이후 호출될 때마다 처음 정해진 this 바인딩을 가지고 호출
const bound = bar.bind(test);
bound(); // 20
```

#### 1.4 new 바인딩

- 자바스크립트의 new 키워드는 함수를 호출할 때 앞에 new 키워드를 사용하는 것으로 객체를 초기화할 때 사용하는데, 이때 사용되는 함수를 생성자 함수라고 합니다.
- 생성자 함수에서는 this 키워드를 해당 생성자를 이용해 생성할 객체에 대한 참조로 사용합니다
- 아래 코드에서 test 함수가 new 키워드와 함께 호출되는 순간 새로운 객체가 생성되고, 새로 생성된 객체가 this로 바인딩됩니다. 그리고 생성된 객체의 a라는 프로퍼티에 20이라는 값이 할당되고, 해당 객체는 test라는 변수에 할당됩니다.

```
function Test() {
  this.a = 20;
}

const test = new Test();

console.log(test.a); // 20
```

#### 1.5 화살표 함수

- ES6에 추가된 화살표 함수(Arrow Function)는 this를 바인딩할 때 앞서 설명한 규칙들이 적용되지 않고, this에 어휘적 스코프(Lexical scope)가 적용됩니다
- 화살표 함수를 정의하는 시점의 컨텍스트 객체가 this에 바인딩 됩니다

```js
const test = {
  a: 20,
  bar: function () {
    setTimeout(() => {
      console.log(this.a);
    }, 1);
  },
};

test.bar(); // 20
```
