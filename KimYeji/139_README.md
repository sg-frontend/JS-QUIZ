## 🔎 문제 코드

```js
class Counter {
  #number = 10;

  increment() {
    this.#number++;
  }

  getNum() {
    return this.#number;
  }
}

const counter = new Counter();
counter.increment();

console.log(counter.#number);
```

## ✅ 해설

```js
class Counter {
  #number = 10; // private 필드 선언

  increment() {
    this.#number++; // 클래스 내부에서 접근 가능
  }

  getNum() {
    return this.#number; // 클래스 내부 접근 가능
  }
}

const counter = new Counter();
counter.increment();

//  클래스 외부에서 private 필드 직접 접근 불가능
console.log(counter.#number);
```

## 🧠 관련 개념

### `#` - Private Fields

ES2022 문법으로 도입되었고 #fieldName 형태로 선언하면 해당 필드는 클래스 외부에서 접근할 수 없음.
