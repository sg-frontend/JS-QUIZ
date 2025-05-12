## 🔎 문제 코드

```js
const obj = { 1: "a", 2: "b", 3: "c" };
const set = new Set([1, 2, 3, 4, 5]);

obj.hasOwnProperty("1");
obj.hasOwnProperty(1);
set.has("1");
set.has(1);
```

## ✅ 해설

### 1. 객체 키의 자료형

`const obj = { 1: "a", 2: "b", 3: "c" };` 코드를 통해 1, 2, 3이라는 숫자로 키로 사용하고 있는데, 자바스크립트에서는 내부적으로 객체 키가 숫자인 경우에 문자열로 변환하여 저장함.

그렇기 때문에 `hasOwnProperty` 를 통해 검사할 때 모두 true를 반환함.

### 2. Set

Set은 고유한 값을 저장하고 값 자체를 그대로 저장함. 따라서 1이 문자열로 변환되지 않고 숫자 1 자체로 저장되기 때문에 `has`를 통해 검사할 때 각각 false / true 값을 반환함.

### 3. 실행 결과

```js
obj.hasOwnProperty("1"); // true (key가 문자열로 저장)
obj.hasOwnProperty(1); // true
set.has("1"); // false (문자열 1 값은 없음)
set.has(1); // true
```

## 🧠 관련 개념

### `hasOwnProperty`

객체가 특정 자신의 속성 값을 가지고 있는지 확인하는 메서드임. 프로토타입 체인에 대한 속성은 확인하지 않음

(있는 경우 - true 반환 / 없는 경우 - false 반환)

### `Set`

중복되지 않는 값을 저장하는 컬렉션임. 추가된 값들은 모두 고유해야하고, 값을 형변환 없이 그대로 + 순서대로 저장함.

Set을 통한 값 비교를 할 땐, `===` 를 사용함.
