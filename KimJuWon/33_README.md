## 🔎 문제 코드

What's the output?

```js
const person = { name: "Lydia" };

function sayHi(age) {
  return `${this.name} is ${age}`;
}

console.log(sayHi.call(person, 21));
console.log(sayHi.bind(person, 21));
```

## ✅ 해설

D | Lydia is 21, function

call()

- sayHi.call(person, 21)은 즉시 실행하여 결과를 반환합니다.
- call() 메서드는 함수를 호출하면서 this를 지정할 수 있습니다.
- 결과: Lydia is 21

bind()

- sayHi.bind(person, 21)은 새로운 함수를 반환합니다.
- bind() 메서드는 바인딩된 함수를 반환할 뿐 실행하지 않습니다.
- 결과: function

## 🧠 관련 개념

### call과 bind
