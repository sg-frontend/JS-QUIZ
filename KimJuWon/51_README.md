## 🔎 문제 코드

```js
function getInfo(member, year) {
  member.name = "Lydia";
  year = "1998";
}

const person = { name: "Sarah" };
const birthYear = "1997";

getInfo(person, birthYear);

console.log(person, birthYear);
```

## ✅ 해설

A | {name:"Lydia"},"1997"

- person는 객체형이고 birthYear는 문자열입니다.
- birthYear는 호출시 값이 복사되어 전달되고 getInfo(person, birthYear)에서 year 매개변수는 '1997'이라는 값을 복사 받습니다
- 따라서 함수내부에서 값을 변경하더라도 원래의 변수에 영행이 없습니다.
- person은 함수 호출시 객체의 참조 주소가 전달됩니다
- 함수 내부에서 객체 속성을 바꾸면 원본 객체도 바뀝니다

## 🧠 관련 개념

### 1. 데이터 타입

- 기본형 데이터 타입: string, number, boolean, null, undefined, symbol, bigint
  - 값 자체가 복사되어 전달
  - 함수 내부에서 수정해도 원래 변수에는 영향 없음
- 참조형 데이터 타입: object, array, function
  - 참조 주소가 복사되어 전달
  - 함수 내부에서 수정하면 원래 객체도 변경
