# this

객체는 상태를 나타내는 프로퍼티와 동작을 나타내는 메서드를 하나의 논리적인 단위로 묶은 복합적인 단위구조이다.

동작을 나타내는 메서드는 자신이 속한 객체의 상태, 즉 프로퍼티를 참조하고 변경할 수 있어야 한다. 이때 메서드가 자신이 속한 객체의 프로퍼티를 참조하려면 먼저 자신이 속한 객체를 가리키는 식별자를 참조할 수 있어야 한다. 따라서 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 특수한 식별자가 필요하다. 이를 위해 자바스크립트는 this라는 특수한 식별자를 제공한다. 

this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수다. this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.

### 함수 호출 방식에 따른 this 바인딩 값

this가 가리키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.

함수를 호출하는 방법에는 4가지가 있는데 각 방법에 따라 바인딩되는 값이 달라진다.

#### **[ 일반 함수 호출 ]**

기본적으로 this에는 전역 객체가 바인딩된다. 일반 함수로 된 모든 함수(중첩 함수, 콜백 함수 포함) 내부의 this에는 전역 객체가 바인딩된다.

#### **[ 메서드 호출 ]**

메서드 내부의 this에는 메서드를 호출할 체, 즉 메서드를 호출할 때 메서드 이름 앞의 마침표(.)연산자 앞에 기술한 객체가 바인딩된다. 즉 메서드 내부의 this는 메서드를 소유한 객체가 아닌 메서드를 호출한 객체에 바인딩된다.

#### **[ 생성자 함수 호출 ]**

생성자 함수 내부의 this에는 생성자 함수가 (미래에) 생성할 인스턴스가 바인딩된다.

#### **[ Functon.prototype.apply/call/bind 메서드에 의한 간접 호출 ]**

Function.prototype.apply/call/bind 메서드에 첫번째 인수로 전달한 객체가 바인딩된다.