# useMemo, useCallback

useMemo와 useCallback에 대해서 알아보기 전에 Memoization이라는 개념을 먼저 알아보자.

### Memoization

메모이제이션은 기존에 수행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법이다.

중복 연산을 피할 수 있기 때문에 메모리를 조금 더 쓰더라도 애플리케이션의 성능을 최적화할 수 있다.



### **[ useMemo는 메모이제이션된 '값'을 반환하고, useCallback은 메모이제이션된 '함수'를 반환한다. ]**

## useMemo

useMemo는 메모이제이션된 '값'을 반환한다.

```javascript
useMemo(() => fn, [deps])
```

여기서 deps로 지정한 값이 변하게 된다면 () => fn 함수를 실행하고, 그 함수의 반환 값을 반환해준다.

**useMemo를 쓰는 이유는 무엇일까요?**

리액트는 state값이 변할 때마다 리렌더링 되는데 만약 복잡한 연산을 하게 되면 시간이 오래걸릴 수도 있습니다. 그래서 특정값 deps가 변할 경우에만 연산을 실행할 수 있도록 useMemo를 사용해 deps라는 변수에 의존하도록 등록하는 것이다. 즉, 리렌더링이 발생할 경우, 특정 변수가 변할 때에만 useMemo에 등록한 함수가 실행되도록 처리하면 불필요한 연산을 하지 않게 된다

**유의사항**

모든 함수를 useMemo로 감싸게 되면 이 또한 리소스 낭비가 될 수 있기때문에, 퍼포먼스 최적화가 필요한 연산량이 많은 곳에 사용하는 것이 좋다.



## useCallback

메모이제이션된 '함수'를 반환한다.

```javascript
useCallback(fn, [deps])
```

useCallback 또한 deps, 의존성이 있는 값이 변하면 fn에 등록된 함수를 반환하는 기능을 가지고 있다.

그렇다면 useCallbakck은 언제 쓰일 수 있을까? 함수가 재생성 되는 것을 방지하기 위해 사용되는데, 다음 예제를 보자.

**자식 컴포넌트에 props로 함수를 전달한 경우**

부모를 통해 props에 함수를 전달받은 자식 컴포넌트에서는 props가 변경되었다고 판단해 리렌더링이 발생하게 된다.

```javascript
function App() {
  const [name, setName] = useState('');
  const onSave = () => {};

  return (
    <div className="App">
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <Profile onSave={onSave} />
    </div>
  );
}
```

useCallback을 사용하지 않으면, name이 변경되어 리렌더링이 발생하면 onSave함수가 새로 만들어지고, Profile 컴포넌트의 props로 onSave함수가 새로 전달하게 된다. 이때 Profile 컴포넌트에서 useMemo를 사용해도 이전 onSava와 이후 onSave가 같은 값을 반환하지만 참조가 다른 함수가 되어버리기 때문에 리렌더링이 일어나게 된다. 

부모 컴포넌트만 수정하려고 했지만 연쇄적으로 하위 컴포넌트들 모두 렌더링이 일어나게 된다.

이럴 때 useCallback을 사용해서 onSave라는 함수를 재사용하는 것으로 자식 컴포넌트의 리렌더링을 방지 할 수 있다.



