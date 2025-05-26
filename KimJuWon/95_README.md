## 🔎 문제 코드

<!-- prettier-ignore-start -->
```js
function nums(a, b) {
  if (a > b) console.log("a is bigger");
  else console.log("b is bigger");
  return;
  a + b;
}

console.log(nums(4, 2));
console.log(nums(1, 2));
```
<!-- prettier-ignore-end -->

## ✅ 해설

B | a is bigger, undefined and b is bigger, undefined

- 함수에서 `return;` 다음에 `a + b;` 코드가 있지만, JavaScript는 개행(줄바꿈)을 만나면 자동으로 세미콜론을 삽입합니다
- 따라서 코드는 실제로 `return;`으로 해석되어, `a + b;` 코드는 실행되지 않는 죽은 코드가 됩니다
- 명시적 반환값이 없는 `return;`은 `undefined`를 반환합니다

## 🧠 관련 개념

### Automatic Semicolon Insertion (ASI)

- JS에서는 세미콜론을 생략할 수 있지만 그렇다고 해서 세미콜론이 없는 것은 아닙니다
- JS 엔진이 자동으로 세미콜론을 삽입하기 때문에 특정 조건에서 의도치 않은 동작을 할 수 있습니다

### 💡 추가 개념: ASI의 적용 규칙

#### ASI가 적용되는 주요 상황

- **var, let, const**: 변수 선언
- **Expression statements**: 표현식 문장
- **do ... while**: 반복문
- **continue, break, return, throw**: 제어문
- **debugger**: 디버깅 문
- **Class field declarations**: 클래스 필드 선언
- **import, export**: 모듈 가져오기/내보내기

#### ASI의 세 가지 주요 적용 규칙

1. **문법 오류 방지를 위한 삽입**

   - 문법적으로 허용되지 않는 토큰이 나왔으며, 이전 토큰과 적어도 하나의 라인 종료자(개행 등)로 나누어진 상황
   - 또는 다음 토큰이 `}`인 경우에도 삽입됩니다

<!-- prettier-ignore-start -->

   ```js
   // 자동 삽입 전
   {
     1
     2
   }
   3

   // 자동 삽입 후
   {
     1;
     2;
   }
   3;
   ```

   <!-- prettier-ignore-end -->

2. **입력 스트림 종료 시 삽입**
   - 코드의 끝에 도달했을 때, 파서가 해당 입력을 완전한 프로그램으로 해석할 수 없는 경우

<!-- prettier-ignore-start -->
```js
// 자동 삽입 전
function greet() {
  console.log("Hello")
}

// 자동 삽입 후
function greet() {
  console.log("Hello");
}
```
<!-- prettier-ignore-end -->

3. **제한된 위치에서 개행 발생 시 삽입**

   - 문법적으로 라인 종료자가 허용되지 않는 위치에 있을 때
   - **return, break, continue, throw 문 다음에 개행이 있는 경우가 가장 흔한 함정**

   <!-- prettier-ignore-start -->

   ```js
   // 의도
   return;
   a + b;

   // 실제 해석
   return;
   a + b;
   ```

   <!-- prettier-ignore-end -->

### 💡 ASI로 인한 일반적인 문제 상황

#### 1. return 문 다음 줄바꿈

<!-- prettier-ignore-start -->
```js
// 의도: a+b 반환
function add(a, b) {
  return
    a + b;  // 죽은 코드!
}
// 실제: 항상 undefined 반환
```

<!-- prettier-ignore-end -->

#### 2. 배열 리터럴 시작 시

<!-- prettier-ignore-start -->
```js
// 의도: a 함수 호출 후 배열 접근
a
[1, 2].forEach(console.log)

// 실제 해석: a[1, 2].forEach(console.log)
// a[1, 2]는 a[2]와 동일 (콤마 연산자)
```
<!-- prettier-ignore-end -->

#### 3. 연산자로 시작하는 줄

<!-- prettier-ignore-start -->
```js
// 의도: 두 표현식을 더함
const x = 1
+ 2

// 실제 해석: const x = 1; +2;
// x는 1이 되고, +2는 별도의 문장으로 평가됨

```

<!-- prettier-ignore-end -->
