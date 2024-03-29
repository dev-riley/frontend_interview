# 프로토타입

자바스크립트는 흔히 프로토타입 기반 언어라 불리는데, 모든 객체들이 자신의 부모 역할을 담당하는 객체와 연결되어 있다. 그리고 부모 객체의 프로퍼티 또는 메서드를 상속받아 사용할 수 있다. 이러한 부모 객체를 프로토타입 객체라고 한다.

자바스크립트의 모든 객체는 [[prototype]]이라는 인터널 슬롯을 가지는데, [[prototype]]의 값은 null 또는 객체이며 상속을 구현하는데 사용된다. 

### [[Prototype]] vs prototype 프로퍼티

모든 객체는 자신의 프로토타입 객체를 가리키는 [[prototype]] 인터널 슬롯을 갖으며 상속을 위해 사용된다.

함수도 객체이므로 [[Prototype]]인터널 슬롯을 가진다. 그런데 함수 객체는 일반 객체와는 달리 prototype 프로퍼티도 소유하게 된다.

이 둘은 다르다. 둘 모두 프로토타입 객체를 가리키지만 관점의 차이가 있다.

**[[Prototype]]** 인터널 슬롯

- 함수를 포함한 모든 객체가 가지고 있는 인터널 슬롯이다.
- 객체의 입장에서 자신의 부모 역할을 하는 프로토타입 객체를 가리키며 함수 객체의 경우 Function.prototype을 가리킨다.

**prototype 프로퍼티**

- 함수 객체만 가지고 있는 프로퍼티다.
- 함수 객체가 생성자로 사용될 때 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체(프로토타입 객체)를 가리킨다.

### 프로토타입 체인

자바스크립트는 객체의 프로퍼티나 메서드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티나 메서드가 없다면 [[Prototype]] 내부 슬롯의 참조를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메서드를 순차적으로 검색한다. 이를 프로토타입 체인이라 한다. 

프로토타입 체인 동작 조건은 객체의 프로퍼티를 참조하는 경우에 해당 객체에 프로퍼티가 없으면 프로토타입 체인이 동작한다.

객체의 프로퍼티에 값을 할당하는 경우에는 프로토타입 체인이 동작하지 않는다. 이는 객체에 해당 프로퍼티가 있는 경우는 값을 재할당하고, 없는 경우에는 해당 객체에 프로퍼티를 동적으로 추가하기 때문이다. 

프로토타입 체인은 자바스크립트가 객체 지향 프로그래밍의 상속을 구현하는 메커니즘이다. 프로토타입 체인의 가장 최상위 객체는 언제나 Object.prototype이다.