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

### 1. 일반 함수 <-> 화살표 함수

`diameter()`는 일반 함수이기 때문에 호출한 shape 객체를 this로 바인딩함. (this.radius == shape.radius)

`perimeter`는 화살표 함수이기 때문에 자기 자신만의 this를 가지지 않고 상위 스코프의 this를 사용함. (shape 객체보다 상위 객체 전역 this를 참조하는데 외부 스코프에 radius 속성이 없음.)

### 2. 실행 결과

```js
console.log(shape.diameter()); // 일반 함수 - 20
console.log(shape.perimeter()); // 화살표 함수 - NaN
```

## 🧠 관련 개념

### this

`this`는 현재 코드의 실행 문맥에 따라 참조 대상을 동적으로 결정하는 변수임.

- **메소드 내부**
  - this :해당 메소드를 호출한 객체 참조
- **일반 함수**
  - this : 호출한 객체에 따라 결정
- **화살표 함수**
  - this : 선언 위치의 상위 스코프의 this 사용
- **생성자 함수**
  - this : 새로운 객체를 참조함
