# Webpack, Babel, Polyfill

### webpack이란? 

번들링과 컴파일을 결합하는 "정적 모듈 번들"

번들링 기능이 있는 번들러에는 여러 가지가 있지만 대표적으로 웹팩이 있다. 가장 많이 사용되는 번들러이기도 하고 웹팩은 자바스크립트 파일 뿐만 아니라 모든 형식의 파일을 모듈로 관리한다는 특징이 있다.

웹팩의 주 목적은 클라이언트에서 자바스크립트 파일을 묶어서 하나의 파일로 사용하기 위함이다.

[ 웹팩의 구성 요소 ]

시작점(Entry Point) : 각 모듈들이 바라보는 최상위 자바스크립트 파일을 정의한다. 즉, 웹팩은 하나의 시작점으로부터 의존적인 모듈을 전부 찾아내서 하나의 파일로 만드는 것이다.

Output : 번들링 결과물을 어디에 생성하고 네이밍할지 정의한다.

Loader : JS가 아닌 여러 가지 타입의 파일(HTML, CSS, 이미지, 폰트 등)들을 웹팩이 이해할 수 있도록 해준다. 여기에 더해 ES6 문법을 ES5로 바꾸어주기도 한다. 웹팩은 JS만 이해할 수 있기 때문에 이러한 과정이 필요하다.

Plugins : 번들링 된 결과물에 대해 적용할 수 있는 속성. 즉, 결과물의 형태를 바꾸는 역할을 한다. ex) 코드 난독화, css to js파일을 별도의 번들로 분리 



------

! 번들링 !

여러 개로 흩어져 있는 파일들을 압축, 난독화 등을 하여 하나의 파일로 모아주는 역할을 한다. 

자바스크립트는 원래 모듈이라는 개념이 없고 하나의 파일에 모든 코드를 담았다.하지만 그러기에는 코드 양이 방대해지기도 하고, 가독성도 떨어지고 무엇보다 웹 애플리케이션이 예전보다 훨씬 복잡하고 고도화되어져서 모듈패턴이 생기게 된 것이다.

모듈 패턴은 전체 애플리케이션의 일부를 독립된 코드로 분리한 것을 말하는데, 이 방식도 한계가 있다. 프로그램이 커질수록 세분화된 파일이 많아지므로 각 변수들의 스코프나 호출 시 발생하는 네트워크 비용에 더 신경써야 하는 것이다.

이 모듈의 문제점을 보완하기 위해 나온것이 번들링이다. 기능별로 모듈화된 파일을 다시 하나로 묶어주는 것이다. 

번들링하게되면 리소스 요청을 나눠진 파일로 인해 여러번 해야했던 것을 한 번만 요청하므로 네트워크 비용이 줄어들게 되고, 단순히 번들링 역할만 하는 것이 아니라 코드 난독화, 용량 압축, 최적화 등을 지원하기 때문에 성능 향상, 보안에도 도움이 된다. 또한 ES6 문법을 ES5로 변환해주는 기능이 있다.(babel)

------

### Babel이란?

대표적인 트랜스파일러이다.

트랜스 파일링이란, 특정 언어로 작성된 코드를 비슷한 다른 언어로 변환시키는 것이다.  트랜스파일러가 필요한 이유는 모든 브라우저가 ES6의 기능(최신 기능)을 제공하지 않기 때문에 ES5코드(구기능)으로 변환시키는 과정이 필요하기 때문이다. 웹팩과 같은 모던 프로젝트 빌드 시스템은 코드가 수정될 때마다 자동으로 트랜스파일러를 동작시켜준다.

바벨의 또 다른 역할로는 **폴리필**이 있다. 개발자는 스크립트에 새로운 함수를 추가하거나 수정해서 스크립트가 최신 표준을 준수할 수 있게 작업할 수 있다. 이렇게 변경된 표준을 준수할 수 있게 기존 함수의 동작 방식을 수정하거나, 새롭게 구현한 함수의 스크립트를 폴리필이라 부른다. 쉽게말하면, 폴리필은 브라우저가 지원하지 않는 기능들의 구현을 채워주는 스크립트이다. 예를 들어, 바벨은 ES5문법으로 번역을 해주지만, ES5에 존재하지 않는 ES6의 Map이나, promise는 번역을 해 줄 수가 없다. 그래서 이 부분을 메꾸기 위해 polyfill을 사용한다. map이나 promise등을 사용가능한 객체로 바꿔준다.

babel은 원래 babel-polyfill을 사용하면 되었지만 지금은 deprecated 되어서 babel 내부에 탑재되어있는 core-js 라이브러리로 ES6 이후의 문법들을 폴리필 처리할 수 있다. regenerator-runtime

babel-loader 패키지는 웹팩에서 babel을 loader로 사용하기 위한 것이다.