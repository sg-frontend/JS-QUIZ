## 🔎 문제 코드

```js
// index.js
console.log("running index.js");
import { sum } from "./sum.js";
console.log(sum(1, 2));

// sum.js
console.log("running sum.js");
export const sum = (a, b) => a + b;
```

## ✅ 해설

sum.js가 먼저 실행 -> index.js가 실행

## 🧠 관련 개념

### 모듈 실행 순서

1. 모듈이 처음 import 될 때 실행
2. 모듈의 코드는 최상위 레벨에서 실행
3. import 된 모듈이 먼저 실행
