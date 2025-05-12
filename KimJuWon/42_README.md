## 🔎 문제 코드

What does the setInterval method return in the browser?

```js
setInterval(() => console.log("Hi"), 1000);
```

## ✅ 해설

A | a unique id

- 위의 코드에서 setInterval()은 1초(1000밀리초)마다 Hi를 출력합니다
- setInterval()은 **고유 ID(숫자)**를 반환합니다.
- 이 ID는 나중에 clearInterval() 함수를 사용하여 해당 간격을 중지하는 데 사용됩니다.

## 🧠 관련 개념

### setInterval

#### 반환값

- 반환된 intervalID는 setInterval() 호출로 생성된, 타이머를 식별하는 0이 아닌 숫자 값입니다. 이 값은 clearInterval()에 전달되어 interval을 취소할 수 있습니다.
