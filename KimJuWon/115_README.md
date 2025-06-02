## 🔎 문제 코드

Which method(s) will return the value 'Hello world!'?

```js
const myMap = new Map();
const myFunc = () => "greeting";

myMap.set(myFunc, "Hello world!");

//1
myMap.get("greeting");
//2
myMap.get(myFunc);
//3
myMap.get(() => "greeting");
```

## ✅ 해설

- 1번: undefined (키가 'greeting' 문자열이 아니라 myFunc 함수)
- 2번: 'Hello world!' (올바른 함수 참조)
- 3번: undefined (새로운 함수 객체 생성)

### 2번과 3번의 차이점: 함수 참조 vs 새로운 함수 생성

```jsx
const myFunc = () => "greeting"; // 함수 정의 및 참조 저장

// 2번: 기존 함수 참조를 사용합니다
myMap.get(myFunc); // myFunc 변수가 가리키는 함수 객체

// 3번: 새로운 함수 객체를 생성합니다
myMap.get(() => "greeting"); // 매번 새로운 함수 객체 생성
```

## 🧠 관련 개념
