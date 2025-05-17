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

B | running sum.js, running index.js, 3

- import 구문으로 특정 변수나 함수만 가져와도 모듈 파일 전체가 먼저 실행됩니다

## 🧠 관련 개념

### import의 호이스팅

- import 구문은 파일의 최상단으로 호이스팅됩니다
- 모듈을 가져오는 과정에서 이는 한 번만 로드되며, 그후에는 캐시된 결과를 사용하게됩니다
- 모듈을 가져올때 필요한 모든 의존성 파일이 먼저 실행된 후에 가져오느 모듈을 사용하는 코드가 실행됩니다.
