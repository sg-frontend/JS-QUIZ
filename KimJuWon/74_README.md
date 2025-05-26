## 🔎 문제 코드

```js
function addToList(item, list) {
  return list.push(item);
}

const result = addToList("apple", ["banana"]);
console.log(result);
```

## ✅ 해설

B | 2

1. list.push(item)는 ["banana"] 배열에 "apple"을 추가합니다
2. 만약 addToList에서 list.push(item)을 반한할 경우 push 메서드의 반환값인 배열의 새로운 길이 2를 반환합니다

## 🧠 관련 개념

### push()

- push() 메서드는 배열의 끝에 하나 이상의 요소를 추가하고, 배열의 새로운 길이를 반환합니다.
