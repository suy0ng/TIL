# React Hooks useReducer

### useReducer

> **useState**의 대체함수이다.
- 리엑트 문서
> 

`useReducer`은 State(상태)를 관리하고 업데이트하는 Hook인 `useState`를 대체할수 있는 Hook이다. **다시말해, `useReducer`은 `useState`처럼 상태를 관리하고 업데이트할수있는 Hook이다**

### useReducer 구성요소

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

useState 와 구분되는것은 `dispath`와 `reducer`함수이다. 이둘은 함수인데, 각각의 형태는 다음과 같다

```jsx
dispatch(action)
reducer(state, action)
```

여기서 주목해야할 점은 **dispatch 내부의 action이 reducer의 두번쨰 인자**로 간다는 점이다. reducer의 첫번째 인자(state)는 관리의 대상이 되는 ‘상태 객체’다. **dispatch는 이미 구현 완료된 함수**이기 떄문에 action에 적절한 값을 넣어 주기만 하면 되지만, **reducer는 직접 구현**해줘야 한다.

```
**reducer** -> state를 업데이트 해준다.
**dispatch** -> Reducer에게 요구하는 행위
**action** -> Dispatch(요구)내용
```

### Example 1

```jsx
const initialCount = { count : 0}

function reducer(state, action){
    switch(action.type) {
        case 'INCREASE':
            return {count : state.count + 1};
        case 'DECREASE' :
            return {count : state.count - 1};
        default :
            return state;
    }
}

function ExampleSelf() {
    const [state,dispatch] = useReducer(reducer , initialCount);

    return (
        <div>
            <h2>count : {state.count} </h2>
            <button onClick={() => dispatch({type:'INCREASE' })}>Up!</button>
            <button onClick={() => dispatch({type:'DECREASE'})}>Down!</button>
        </div>
    );
}

export default ExampleSelf;
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aee0cf24-7814-421a-a8bc-6914fcc0a992/Untitled.png)

1 ) Up! 버튼을 눌렀을때 dispatch가 reducer에게 액션을 요구한다. 이때 action.type은 `INCREASE`이니 reducer함수에서 `return {count : state.count + 1}를 하면서 상태를 업데이트한다.

2 ) Down! 버튼을 눌렀을때 dispatch가 reducer에게 액션을 요구한다. 이때 action.type은 `DESCREASE`이니 reducer함수에서 `return {count : state.count + 1}를 하면서 상태를 업데이트한다.

참고 자료 : 

[https://charles098.tistory.com/185](https://charles098.tistory.com/185)

[https://velog.io/@iamhayoung/React-Hooks-useReducer에-대해-알아보기](https://velog.io/@iamhayoung/React-Hooks-useReducer%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0)