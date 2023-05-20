# useMemo

`usememo`는 컴포넌트의 성능을 최적화하는데 사용되는 hook이다.

`usememo`는 컴퓨터가 동일한 계산을 반복해야할때 이전에 계산한 값을 메모리에 넣음 으로서 계산의 반복수행을 제거하여 프로그램 실행속도를 빠르게 하는 것이다

```jsx
function Memoexample() {
    const value = example();
    return (
        <div>{value}</div>
    );
}

function example() {
    return 100 + 100 + 100 - 399
}
```
이 코드에서 페이지가 랜더링이 된다하면 컴포넌트가 초기화가 되어 계속 `example()`함수가 돌아갈 것이다. 때문에 우리는 useMemo 훅을 사용하는 것인데 useMemo를 사용하면 렌더링 => 컴포넌트 함수 호출 => memoize된 함수 재사용하는 순서를 거친다.

그래서 우리는 이 코드를 useMemo를 활용하여 이렇게 고칠수있다.
```jsx
function Memoexample() {
    const value = useMemo(() => {
        return example();
    }, [item])

    return (
        <div>{value}</div>
    );
}

function example() {
    return 100 + 100 + 100 - 399
}
```
이렇게 코드를 고치게 되면 컴포넌트가 다시 랜더링된다해도 example함수를 실행하지 않고 할 것이다.