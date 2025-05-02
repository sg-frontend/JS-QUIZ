7번

new Number(3) 의 타입은 넘버가 아니고, 객체다.

그래서  a = 3 과 b = new Number(3) 일 때, a === b는 false 다.


9번

abc = {} 라고 선언을 하지 않은 채, consle.log(abc) 를 해도 글로벌 객체(node: global, browser: window)에 선언이 된다.


11번 x

13번 x

프로토타입을 통해 함수를 추가해야 다른 인스턴스에서 해당 함수를 사용할 수 있다.

14 x
모든 객체는 프로토타입을 가진다.  false

17번 x

18 x 객체는 참조를 비교한다.

20 x use strict 를 쓰면, 레퍼런스 에러가 뜬다.
