## 🔎 문제 코드

```js
String.prototype.giveLydiaPizza = () => {
  return "Just give Lydia pizza already!";
};

const name = "Lydia";

console.log(name.giveLydiaPizza());
```

A | "Just give Lydia pizza already!"
B | TypeError: not a function
C | SyntaxError
D | undefined

## ✅ 해설

A | "Just give Lydia pizza already!"

- JS의 String은 기본 생성자 함수로 프로토타입 메서드를 추가할 수 있습니다
- String.prototype.giveLydiaPizza 메서드를 정의하면 모든 문자열에서 접근할 수 있습니다.
- 원시 문자열인 name은 내부적으로 String 객체로 변환되어 메서드에 접근할 수 있습니다.

## 🧠 관련 개념
