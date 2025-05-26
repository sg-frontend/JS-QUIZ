## 🔎 문제 코드

```js
const box = { x: 10, y: 20 };

Object.freeze(box);

const shape = box;
shape.x = 100;

console.log(shape);
```

## ✅ 해설

```js
const box = { x: 10, y: 20 };

Object.freeze(box); // box객체를 불변으로 설정함

const shape = box; // box와 같은 객체 참조
shape.x = 100; // 변경되지 않음

console.log(shape);
```

## 🧠 관련 개념

### `Object.freeze()`

- 객체를 불변으로 만듦
- 속성 추가, 삭제, 수정 불가능함
- 얕은 불변성 제공 (데이터가 그대로 생성되는 것이 아닌 해당 데이터의 참조 값(메모리 주소)를 전달하여 결국 한 데이터를 공유)
