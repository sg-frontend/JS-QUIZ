## 🔎 문제 코드

```js
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const member = new Person("Lydia", "Hallie");
Person.getFullName = function () {
  return `${this.firstName} ${this.lastName}`;
};

console.log(member.getFullName());
```

## ✅ 해설

- Person.getFullName은 생성자 함수(Person) 자체에 메서드를 추가한 것이지, **생성된 객체(member)**에 추가한 것이 아닙니다.

- new 키워드를 사용하여 생성된 member 객체에는 getFullName 메서드가 없습니다.

- 따라서 member.getFullName()을 호출하려고 하면 TypeError가 발생합니다.

- 만약 모든 인스턴스에서 공통으로 사용할 메서드를 추가하고 싶다면, 프로토타입을 사용해야 합니다.

## 🧠 관련 개념
