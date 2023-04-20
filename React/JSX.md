# 리액트에서의 JSX 문법

JSX란?

자바스크립트의 확장 문법으로써, 자바스크립트의 공식적인 문법이라고 할 수는 없으나 자바스크립트에서 HTML을 작성하듯이 비슷하게 작성할 수 있도록 해주는 것이다. 

브라우저에서 실행하기 전에 코드가 번들링되는 과정에서 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.



JSX 문법

- 컴포넌트에 여러 요소가 있다면 반드시 부모 요소 하나가 감싸는 형태여야 한다.

  ```javascript
  // 잘못된 예제 : 오류 발생함
  funtion App() {
      return(
      	<h1>안녕</h1>
          <h1>클레오파트라</h1>
      )
  }
  // 옳은 예제
  funtion App() {
      return(
          <div>
      		<h1>안녕</h1>
          	<h1>클레오파트라</h1>
          </div>
      )
  }
  ```

  이렇게 감싸는 이유는 리액트가 사용하는 virtual DOM 방식은 컴포넌트를 감지할 때 효율적으로 비교하거나 컴포넌트 내부는 하나의 DOM 트리 구조로 이루어져야 한다는 규칙이 있기 때문이다.

- 자바스크립트의 값을 JSX 안에서 렌더링 할 수 있다.

  ```javascript
  funtion App() {
      const hi = '안녕';
      return(
          <div>
      		<h1>{hi}</h1>
          	<h1>클레오파트라</h1>
          </div>
      )
  }
  ```

- JSX 내부의 자바스크립트 표현식 내에서는 IF문을 사용할 수 없고, 삼항 연산자를 사용해야 한다.

  ```javascript
  funtion App() {
      const hi = '안녕';
      return(
          <div>
              {hi === '안녕' ? (
  				<h1>안녕</h1>
               	<h1>클레오파트라</h1>
               ) : (
      			<h1> 안녕못함</h1>
      		)}
          </div>
      )
  }
  ```

- undefined를 렌더링하지 않아야 한다.

  ```javascript
  // 안됨. 에러 남
  function App() {
      const hi = undefined;
      retrun hi;
  }
  // OR 연산자로 방지할 수 있음
  function App() {
      const hi = undefined;
      retrun hi || "값이 undefined";
  }
  // 단, JSX 내부에서 undefined를 렌더링하는 것은 에러가 나지 않는다.
  function App() {
      const hi = undefined;
      retrun (
      	<div>{hi}</div>
      )
  }
  ```

- HTML에서 스타일을 지정할 때 background-color와 같이 -문자가 포함된 이름들은 JSX에서 -을 없애고 카멜표기법으로 backgroundColor로 작성해야 함.

- 태그에 class 속성을 설정할 때는 class라는 이름대신 className이라고 표시해야 한다.

  ```javascript
  <div className="##"></div>
  ```

  

