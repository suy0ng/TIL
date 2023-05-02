# React Hooks useRef

React Hooks의 useRef에 대해 알아보자.

### useRef?

> `useRef`는 .current 프로미터로 전달된 인자(initial Value)로 초기화된 변경 가능한 Ref객체를 반환합니다. 반환된 객체는 컴포넌트의 전 생애주기를 통해유지될것입니다. - 리엑트 공식 홈페이지
> 

useRef는 저장공간 또는 DOM요소에 접곤하기 위해 사용되는 React Hook이다. 여기서 Ref는 reference, 즉 참조를 뜻한다.

우리가 JS를 사용할때는 DOM 을 선택하기 위해서 querySelector등의 함수를 사용한다. 하지만 React에서는 useRef라는 React Hook을 사용한다.

### 사용예제

**1 ) useRef사용 예시 - 변수 관리**

```jsx
const [renderer, setRenderer] = useState(0);
  const countRef = useRef(0);
  let countVar = 0;

  const doRender = () => {
    setRenderer(renderer + 1);
  };

  const increaseRef = () => {
    countRef.current = countRef.current + 1;
    console.log("ref :", countRef.current);
  };

  const increaseVar = () => {
    countVar++;
    console.log("var :", countVar);
  };

  const printResults = () => {
    console.log(`ref : ${countRef.current}, var : ${countVar}`);
  };

  return (
    <div>
      <p>Ref : {countRef.current}</p>
      <p>Var : {countVar}</p>
      <button onClick={doRender}>Render!!</button>
      <button onClick={increaseRef}>Ref 올려</button>
      <button onClick={increaseVar}>Var 올려</button>
      <button onClick={printResults}>Ref Var값 출력하기</button>
    </div>
  );
```

Ref와 Var타입으로 만든 예시이다. 여기에서 increaseRef 또는 increaseVar을 실행시키면 화면에는 결과가 뜨지않고 콘솔창에만 출력되는것을 볼수있다. 이를 통해 useRef로 관리하는 값은 값이 변해도 화면이 렌더링되지 않음을 알수있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac620eeb-6238-4f03-a7ce-39fb473fed29/Untitled.png)

그리고 렌더링을 시키는 Render!! 버튼을 누르게 되면 다음과 같은 현상이 일어나는 것을 확인할수 있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f3d849b-1847-4e2b-af7b-71763bef49b1/Untitled.png)

Ref의 값은 업데이트 되었으나 Var값은 0으로 초기화된것을 확인할수있다.  렌더링 하면서 `let countVar = 0;` 코드가 실행되면서 let countVar은 초기화 되었으나 ref값은 그대로인것을 확인할수 있다.

 **2) useRef사용 예시 - DOM 요소 선택**

```jsx
import React, { useEffect, useRef } from "react";

function Example4(props) {
  const inputRef = useRef();

  useEffect(() => {
    // console.log(inputRef);
    inputRef.current.focus();
  }, []);

  const logIn =() => {
    alert(`환영합니다.${inputRef.current.value}`)
    inputRef.current.focus();
  }

  return (
    <div>
      <input ref={inputRef} placeholder="username" type="text" />
      <button onClick={logIn}>로그인</button>
    </div>
  );
}
```

다음과 같이 사용하면 input태그의 내용을 ref로 관리할수있게된다.