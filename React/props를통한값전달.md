# props 를 통해 컴포넌트에게 값 전달
이번에는 컴포넌트의 `props` 라는 개념에 대해서 알아보겠습니다. `props` 는 `properties` 의 줄임말이다. 우리가 어떠한 값을 컴포넌트에게 전달해줘야 할 때, `props` 를 사용한다.

### props의 기본 사용법

예시를 들어서 Hello에 name이란 `props`를 전달해보겠다.

**src/app.js**

```jsx
import React from "react";
import Hello from "./Hello.js";
import "./App.css";

function App() {
  return (
    <div>
      <Hello name='react' />
    </div>
  );
}

export default App;
```

이제 Hello 컴포넌트에서 name이라는 `props`를 사용해보겠다.

**src/Hello.js**

```jsx
import React from 'react';

function Hello(props) {
    return (
        <div>
            안녕하세요 {props.name}
        </div>
    );
}

export default Hello;
```

컴포넌트에게 전달되는 props는 파라미터를 통해 확인할수있으며 props는 객체형태로 전달된다, 만약 `name`값을 조회하고 싶다면 `props.name`을 통해 전달 받아 사용할수있다.

### 여러개 props전달, 비구조화 할당

Hello 컴포넌트에 또 다른 props인 `color`를 전달해 보겠습니다.

```jsx
import React from "react";
import Hello from "./Hello.js";
import "./App.css";

function App() {
  return (
    <div>
      <Hello name='react' color='red' />
    </div>
  );
}

export default App;
```

그 다음에는 Hello컴포넌트에서 받은 color로 글씨 색상을 변경해보도록하겠 습니다.

```jsx
import React from 'react';

function Hello(props) {
    return (
        <div style={{ color : props.color}}>
            안녕하세요 {props.name}
        </div>
    );
}

export default Hello;
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5ba844f3-702f-4f84-9999-0877c3a13438/Untitled.png)

와 같이 얻을수 있다 하지만 이러면 `props.`를 계속사용하고 있다. 비구조화 할당문법을 사용하면 조금더 코드를 간결하게 쓸수있다.

```jsx
import React from 'react';

function Hello({name , color}) {
    return (
        <div style={{ color : color}}>
            안녕하세요 {name}
        </div>
    );
}

export default Hello;
```

위와 같이 사용해주면 된다. 

### defaultprops 로 기본값 설정

컴포넌트에 props를 지정해주지 않았다면 기본적으로 값을 설정하고 싶다면 `defaultprops`를 지정해주면 된다. 

```jsx
import React from 'react';

function Hello({name , color}) {
    return (
        <div style={{ color : color}}>
            안녕하세요 {name}
        </div>
    );
}

Hello.defaultProps = {
    name: '이름 없음',
    color : 'black'
}

export default Hello;
```

App.js도 수정해주겠다.

```jsx
import React from "react";
import Hello from "./Hello.js";
import "./App.css";

function App() {
  return (
    <div>
      <Hello name='react' color='red' />
      <Hello />
    </div>
  );
}

export default App;
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6be06e71-74e4-4c14-9949-274fbf9d8e0b/Untitled.png)

와 같은 결과값을 얻을수 있다.

### props.children

컴포넌트 태그안의 값을 조회하고 싶을때에는 `props.childrend`을 사용하면 된다.이번에는 `props.children`을 사용하는 새로운 컴포넌트를 생성하겠다.

**src/Wrapper.js**

```jsx
import React from 'react';

function Wrapper() {
    const style = {
        border : '2px solid black',
        margin : '16px'
    }
    
    return (
        <div style={style}>
            
        </div>
    );
}

export default Wrapper;
```

이 컴포넌트를 App.js에서 사용해보겠다.

```jsx
import React from "react";
import Hello from "./Hello.js";
import Wrapper from "./Wrapper.js";
import "./App.css";

function App() {
  return (
    <Wrapper>
      <Hello name='react' color='red' />
      <Hello />
    </Wrapper>
  );
}

export default App;
```

Wrapper componentr안에 Hello 컴포넌트를 2개를 사용을 했다. 하지만 브라우저에서는 다음과 같이 될것이다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc79532e-fb06-4de6-a1a4-333e48513822/Untitled.png)

내부의 내용을 보이게 하려면 Wrapper.js 에서 `props.children` 을 렌더링해줘야한다,

```jsx
import React from 'react';

function Wrapper({children}) {
    const style = {
        border : '2px solid black',
        margin : '16px'
    }

    return (
        <div style={style}>
            {children}
        </div>
    );
}

export default Wrapper;
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/186894dd-35f8-4ff3-afe5-eeb7b9aa5331/Untitled.png)