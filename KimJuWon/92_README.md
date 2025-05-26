# 함수 선언 vs 화살표 함수: prototype과 그 이상의 차이점

## 🔎 문제 코드

What's the output?

```js
function giveLydiaPizza() {
  return "Here is pizza!";
}

const giveLydiaChocolate = () => "Here's chocolate... now go hit the gym already.";

console.log(giveLydiaPizza.prototype);
console.log(giveLydiaChocolate.prototype);
```

## ✅ 해설

D | { constructor: ... } undefined

함수 선언 방식으로 정의된 함수는 prototype 속성을 가지지만 화살표 함수 방식으로 정의된 함수는 prototype을 가지지 않습니다

## 🧠 관련 개념

### 함수 선언과 화살표 함수의 차이점

#### 1. 함수 선언

- 함수 선언 방식으로 정의된 함수는 prototype 속성을 가지고 이는 Function.prototype을 상속받아 { constructor: ... } 형태를 가집니다
- 함수 선언으로 만든 함수는 내부적으로 Function 객체의 인스턴스이고, 모든 함수 객체는 프로토타입 속성을 가지며 이 속성은 빈 객체로 초기화됩니다 -> { constructor: ... } 형식을 가지는 객체가 자동으로 할당

#### 2. 화살표 함수

- 화살표 함수는 prototype 속성을 가지지 않습니다 -> giveLydiaChocolate.prototype은 undefined
- 화살표 함수는 생성자 함수로 사용될 수 없기 때문에 일반함수와 다르게 prototype 속성을 가지지 않게 설계되었습니다

### 💡 추가 개념: 함수 선언과 화살표 함수의 차이점

#### 1. this 바인딩 차이

- **일반 함수**: 자신이 호출된 컨텍스트에 따라 this가 동적으로 결정됩니다

  ```js
  const obj = {
    name: "Object",
    regularFunc: function () {
      console.log(this.name); // "Object" 출력
    },
  };
  obj.regularFunc();

  const standalone = obj.regularFunc;
  standalone(); // undefined 출력 (전역 객체에 name 속성이 없을 경우)
  ```

- **화살표 함수**: 선언될 때의 렉시컬 스코프의 this를 유지합니다(lexical this)
  ```js
  const obj = {
    name: "Object",
    arrowFunc: () => {
      console.log(this.name); // 외부 스코프(보통 전역)의 this 참조
    },
  };
  obj.arrowFunc(); // undefined 출력 (화살표 함수는 자신이 선언된 스코프의 this를 사용)
  ```

#### 2. 호이스팅(Hoisting) 차이

- **함수 선언문**: 코드 실행 전에 메모리에 적재되어, 선언 전에도 호출 가능합니다

  ```js
  // 이것이 가능합니다
  sayHello(); // "Hello" 출력
  function sayHello() {
    console.log("Hello");
  }
  ```

- **화살표 함수**: 변수 선언만 호이스팅되고 초기화는 되지 않아 TDZ(Temporal Dead Zone)에 영향을 받습니다
  ```js
  // 이것은 에러 발생
  sayHi(); // ReferenceError: Cannot access 'sayHi' before initialization
  const sayHi = () => console.log("Hi");
  ```

#### 3. arguments 객체

- **일반 함수**: arguments 객체에 접근할 수 있습니다
  ```js
  function sum() {
    let total = 0;
    for (let i = 0; i  {
    return args.reduce((total, num) => total + num, 0);
  };
  console.log(sum(1, 2, 3)); // 6 출력
  ```

#### 4. 생성자 함수로서의 사용

- **일반 함수**: new 키워드로 인스턴스 생성 가능

  ```js
  function Person(name) {
    this.name = name;
  }
  const john = new Person("John");
  console.log(john.name); // "John" 출력
  ```

- **화살표 함수**: new 키워드로 인스턴스 생성 불가능
  ```js
  const Person = (name) => {
    this.name = name;
  };
  const john = new Person("John"); // TypeError: Person is not a constructor
  ```

#### 5. 프로토타입과 상속 관계

- **일반 함수의 prototype**: 생성자 속성을 포함한 객체이며, 이 함수를 통해 생성된 객체의 [[Prototype]]에 연결됩니다

  ```js
  function Animal(name) {
    this.name = name;
  }
  Animal.prototype.speak = function () {
    console.log(`${this.name} makes a sound`);
  };

  const dog = new Animal("Dog");
  dog.speak(); // "Dog makes a sound" 출력

  console.log(dog.__proto__ === Animal.prototype); // true
  ```

- **화살표 함수**: prototype 속성이 없으므로 상속 구조를 만들 수 없습니다

#### 6. 메서드 정의 시 활용

- 객체 메서드에서는 일반 함수를 사용하면 this 바인딩 문제가 발생할 수 있습니다
- 콜백 함수나 중첩 함수에서는 화살표 함수를 사용해 외부 this를 유지하는 것이 유리합니다

  ```js
  const counter = {
    count: 0,
    // 메서드로 정의할 때는 일반 함수가 적합
    increment: function () {
      this.count++;

      // 내부 콜백에서는 화살표 함수로 외부 this 유지
      setTimeout(() => {
        console.log(this.count); // 올바르게 counter.count 접근
      }, 1000);
    },
  };
  ```
