## React Hooks - useEffect

React Hooks의 useEffect에 대해서 알아보자

### useEffect ?

- 컴포넌트가 렌더링 될 떄 특정 작업을 실행할 수 있도록 하는 Hook이다.
- 컴포넌트가 마운트 됐을떄(처음 나타날떄), 언마운트 됐을때 ( 사라질떄 ), 그리고 특정 컴포넌트가 업데이트될떄 처리할수있다.

### 사용방법

- 첫 번쨰 인자는 함수, 두번쨰 인자는 배열이 들어간다[deps]

```jsx
import { useEffect } from "react";

useEffect(effect,[deps]);
```

### 1 ) effect

- 렌더링 이후 실행할 함수 ( 리엑트는 이 함수를 기억 했다가 DOM 업데이트 이후 불러낸다)
- Effect함수에서 함수를 return할 경우 그 함수가 컴포넌트가 Unmount 될 때 정리의 개념으로 한 번 실행된다.

```jsx
// 렌더링 될 떄 마다 실행된다. 
    useEffect(() => {
      console.log('상관없이 렌더링 될때마다!⭐')
    })
```

만약 최초 렌더링시에만 실행하고싶으면 다음과 같이 하면 된다.

```jsx
// 처음 마운팅할떄만 실행!
    useEffect(() => {
      console.log('처음 마운팅할떄만! 😒')
    },[])
```

그리고 특정 값이 변경될떄에만 실행하고 싶으면 다음과 같이 하면된다.

```jsx
// 마운트 + [count] 변경될때만 실행된다.
    useEffect(() => {
      console.log('😊숫자 변함')
    },[count])
```

이렇게 되면 최초렌더링 할때 그리고 count값이 변할때마다 실행된다.

### **cleanUp함수**

- useEffect안에서 return할 때 실행 된다. (useEffect 뒷정리를 한다.)
- 만약 컴포넌트가 마운트 될 때 이벤트 리스너를 통해 이벤트를 추가하였다면 컴포넌트가 언마운트 될 떄 이벤트를 삭제 해주어야 한다. 그렇지 않으면 컴포넌트가 리렌더링 될 떄마다 새로운 이벤트 리스너가 헨들러에 바인딩 될것이다. 이는 자주 리렌더링 될 경우 메모리 누수가 발생할 수 있다.

```jsx
useEffect(() => {
    console.log("useEffect!!", count);

    return () => {
      // clean up
      console.log("cleanup!!", count);
    }
  }, [count]);
```