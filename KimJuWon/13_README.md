## 🔎 문제

Q: What are the three phases of event propagation?
Target, Capturing, Bubbling

## ✅ 해설

Capturing > Target > Bubbling

## 🧠 관련 개념

```js
<div onclick="alert('div에 할당한 핸들러!')">
  <em>
    <code>EM</code>을 클릭했는데도 <code>DIV</code>에 할당한 핸들러가 동작합니다.
  </em>
</div>
```

- 위의 코드는 `<em>` 이나 `<code>` 를 클릭하여도 alert가 정상작동합니다

### 1. 버블링

- 이벤트가 상위 요소로 전파되는 단계
- 한 요소에 이벤트가 발생하면 이 요소에 할당된 핸들러가 동작하고 이어서 부모 요소의 핸들러가 동작합니다
- 가장 최상단의 조상 요소를 만날때까지 이 과정이 반복되면서 요소 각각에 할당된 핸들러가 동작합니다.

```js
<form onclick="alert('form')">
  FORM
  <div onclick="alert('div')">
    DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```

- 가장 안쪽의 <p>태그를 클릭하면 순서대로 아래와 같이 발생합니다.

1. <p>에 할당된 onclick 핸들러가 동작합니다.
2. 바깥의 <div>에 할당된 핸들러가 동작합니다.
3. 그 바깥의 <form>에 할당된 핸들러가 동작합니다.
4. document 객체를 만날 때까지, 각 요소에 할당된 onclick 핸들러가 동작합니다.

- 이와 같은 흐름을 이벤트 버블링이라고 부릅니다.

> 거의 모든 이벤트는 버블링이 이루어집니다
> focus 이벤트와 같이 버블링되지 않는 이벤트도 있습니다.

### 2. event.target

- 이벤트가 실제 타깃 요소에 전달되는 단계
- 이벤트가 발생한 가장 안쪽의 요소는 target 요소라고 불리고 event.target을 사용해 접근할 수 있습니다.
- event.target과 this (event.currentTarget)의 차이
  - event.target은 실제 이벤트가 시작된 ‘타깃’ 요소라 버블링이 진행되어도 변하지 않습니다.
  - this는 ‘현재’ 요소로, 현재 실행 중인 핸들러가 할당된 요소를 참조합니다

#### 버블링 중단하기

- 이벤트 버블링은 타깃 이벤트에서 시작해서 <html> 요소를 거쳐 document 객체를 만날 때까지 각 노드에서 모두 발생합니다. 몇몇 이벤트는 window 객체까지 거슬러 올라가기도 합니다
- 핸들러에게 이벤트를 완전히 처리하고 난 후 버블링을 중단하도록 명령할 수도 있습니다.
- event.stopPropagation() 사용
- event.stopPropagation()은 위쪽으로 일어나는 버블링은 막아주지만, 다른 핸들러들이 동작하는 건 막지 못해 버블링을 멈추고, 요소에 할당된 다른 핸들러의 동작도 막으려면 event.stopImmediatePropagation()을 사용해야 합니다

> event.stopPropagation()은 추후에 문제가 될 수 있는 상황
>
> 1. 중첩 메뉴를 만들었다 가정합시다. 각 서브메뉴(submenu)에 해당하는 요소에서 클릭 이벤트를 처리하도록 하고, 상위 메뉴의 클릭 이벤트 핸들러는 동작하지 않도록 stopPropagation을 적용합니다.
> 2. 사람들이 페이지에서 어디를 클릭했는지 등의 행동 패턴을 분석하기 위해, window내에서 발생하는 클릭 이벤트 전부를 감지하기로 결정합니다. 일부 분석 시스템은 그렇게 분석합니다. 이런 분석 시스템의 코드는 클릭 이벤트를 감지하기 위해 document.addEventListener('click'…)을 사용합니다.
> 3. stopPropagation로 버블링을 막아놓은 영역에선 분석 시스템의 코드가 동작하지 않기 때문에, 분석이 제대로 되지 않습니다. 안타깝게도 stopPropagation을 사용한 영역은 '죽은 영역(dead zone)'이 되어버립니다.
>
> - 버블링을 막아야 해결되는 문제라면 대부분 커스텀 이벤트 등을 사용해 문제를 해결할 수 있습니다

### 3. 캡쳐링

- 이벤트가 하위 요소로 전파되는 단계
