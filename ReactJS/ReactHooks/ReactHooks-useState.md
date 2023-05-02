# useState


### useState

상태 관리를 할수있는 Hook이다

**변수 선언하기**

```jsx
const [state,setState ] = useState(초기값);
```

state의 값을 변경하시려면 setState 함수를 불러서 인자에는 변경될 값을 넣어 주면 된다.

```jsx
setState(1);
```

예시 )

```jsx
import { useState } from 'react'
import './App.css';

function App() {
  const [time, setTime] = useState(1);

  const onClick = () => {
    setTime(time + 1);
  }

  console.log('time 업데이트 -> ', time);
  
  return (
    <div className="App">
      <header className="App-header">
        <span>현재시간: {time}시</span>
        <button onClick={onClick}>update</button>
      </header>
  </div>
  );
}

export default App;
```

이렇게 되면 렌더링이 될때마다 time이 값이 업데이트된 state가 들어가는 것을 확인할수 있습니다.