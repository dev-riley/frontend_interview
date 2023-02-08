# Virtual Dom

## DOM이란?

Document Object Model의 약자

웹 페이지를 이루는 태그들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델을 의미한다.

DOM을 문서 객체 모델이라고 하는데 여기서 문서 객체란 html, head, body와 같은 태그들을 javascript가 이용할 수 있는(메모리에 보관할 수 있는) 객체를 의미한다.

즉 DOM은 HTML와 스크립팅 언어(javascript)를 서로 이어주는 역할을 한다.

### [ Virtual DOM을 사용하게 된 이유 ]

큰 규모의 웹 어플리케이션은 수많은 데이터가 로딩된다. 데이터가 로딩될때마다 수많은 요소들이 DOM에 직접 접근하여 변화를 주다 보면 로딩 속도가 느려질 가능성이 크다. 이는 DOM 자체가 느려지는 게 아니다. 웹 브라우저 단에서 DOM 변화가 일어나면 웹 브라우저가 CSS를 다시 연산하고 레이아웃을 구성하고, 페이지를 리페인트하는 과정이 오래걸리는 것이다. (스타일 =>  레이아웃 => 페인트 => 합)

위와 같은 속도 이슈와 많은 일을 수행하다가 버그가 발생하거나 브라우저가 죽는 일 등의 일을 개선하고자 Virtual DOM이 나왔다.

속도 이슈에 대한 해결책은 결국 DOM을 최소한으로 조작하는 방법 밖에는 없다. 그래서 리액트에서는 이 문제점을 해결하기 위해 Virtual DOM 방식을 사용해 DOM의 업데이트를 추상화하여 처리 횟수를 최소한으로 한다.



## Virtual DOM 이란?

virutal DOM은 실제 DOM을 조작하는 게 아니라 메모리에 DOM을 추상화한 자바스크립트 객체를 구상해 사용하는 것이다. 다시 말해, 메모리에 실제 DOM트리와 동일한 트리 구조의 javascript 객체를 가지고 있는 것이다.

### [ 리액트가 virtual DOM을 반영하는 절차 ]

1. 데이터가 업데이트 되면, 전체 UI를 Virtual DOM에 리렌더링함
2. 이전 Virtual DOM에 있던 내용과 현재의 내용을 비교함(가상 돔끼리 비교)
3. 바뀐 부분만 실제 DOM에 적용이 됨 (컴포넌트가 업데이트될 때, 레이아웃 계산이 한번만 이루어)