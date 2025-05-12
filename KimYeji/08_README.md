## 🔎 문제 코드

```js
class Chameleon {
  static colorChange(newColor) {
    this.newColor = newColor;
    return this.newColor;
  }

  constructor({ newColor = "green" } = {}) {
    this.newColor = newColor;
  }
}

const freddie = new Chameleon({ newColor: "purple" });
console.log(freddie.colorChange("orange"));
```

## ✅ 해설

### 1. static 메서드

`colorChange`는 정적 메서드이기 때문에 클래스로 객체를 생성하지 않아도 호출이 가능함.
현재 코드에서 freddie 인스턴스를 생성하고 이를 통해 정적 메서드인 colorChange를 호출하기 때문에 오류가 발생함.

### 2. 실행 결과

```js
console.log(freddie.colorChange("orange")); // TypeError
```

## 🧠 관련 개념

### 정적 메서드 Static Method

`static`키워드로 정의된 메서드는 함수 or 클래스 자체에 속하기 때문에 인스턴스에서 호출할 수 없고 함수 or 클래스에서 호출해야함. 보통 클래스 레벨에서 공통 작업을 수행하는 경우에 많이 사용함.

문제 코드에서 freddie 인스턴스를 생성하는 대신 `Chameleon.colorChange()` 방식으로 해당 정적 메서드를 호출하거나 static 키워드를 삭제하여 인스턴스 메서드로 변경하여 사용할 수 있음.
