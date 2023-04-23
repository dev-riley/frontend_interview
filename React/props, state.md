# props와 state 차이

둘 다 React에서 구성 요소가 데이터를 받거나 처리하고 보내기 위해 사용된다.

### props

부모 컴포넌트로부터 전달되는 데이터이며, 데이터를 변경할 수 없다.  주로 하위 컴포넌트로 값을 전달할 때 많이 사용한다.



### state

컴포넌트의 상태를 나타내며, 컴포넌트 내부에서 생성된다. 데이터 변경이 가능하고 외부에 공개하지 않고 컴포넌트가 스스로 관리한다.

state로 사용하는 것은 컴포넌트의 상태값을 나타내기 위한 값들 예를 들어, 리스트에서 선택된 값, 체크박스에서 체크된 값, 텍스트 박스의 텍스트 등이 있다. 상태에 따라 이러한 값들은 변경이 가능하고, state가 변경되면 컴포넌트를 다시 렌더링 해야한다.