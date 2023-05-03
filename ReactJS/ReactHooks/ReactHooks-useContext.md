# React Hooks useContext

### Context 란?

React 공식문서에 쓰여있는 설명에는, *‘context를 이용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있습니다.’*라고 적혀있다.

> 일반적인 React 어플리케이션에서 **데이터는 props를 통해서 부모에서 자식에게 전달** 되지만, 어플리케이션 안의 여러 컴포넌트들에게 props를 전달해줘야 하는 경우 context를 이용하면 명시적으로 props를 넘겨주지 않아도 값을 고유할수 있게 해주는 것이다.

**한마디로 데이터가 필요할때마다 props를 통해 전달할 필요가없이 context를 이용해 공유한다!**
> 

### Context 예시

```jsx
import React, { createContext } from 'react'

// 0. AppContext 생성
const AppContext = createContext()

const App = () => {
  const user = {
    nickname: 'danuel',
    isAdmin: true
  }

  return (
    <AppContext.Provider value={user}>
      <div>
        <Posts />
      </div>
    </AppContext.Provider>
  )
}

// 1. PostsContext 생성
const PostsContext = createContext()

const Posts = () => {
  const posts = [
    {
      title: 'useContext 알아보기',
      content: '이번 편에서는 React Context를 ...'
    }
  ]

  return (
    <PostsContext.Provider value={posts}>
      <Children />
    </PostsContext.Provider>
  )
}

// 2. user와 posts를 가져와 화면에 보여주기
const Children = () => (
  <AppContext.Consumer>
    {user => (
      <PostsContext.Consumer>
        {posts => {
          let label = 'user'
          if (user.isAdmin) {
            label = 'admin'
          }

          return (
            <div>
              <div>{label}</div>
              <div>{user.nickname}</div>
              <div>{posts.map((post, index) => (
                <div key={index}>
                  <div>{post.title}</div>
                  <div>{post.content}</div>
                </div>
              ))}</div>
            </div>
          )
        }}
      </PostsContext.Consumer>
    )}
  </AppContext.Consumer>
)
```

React Context는 Props Drilling 패턴을 떨칠 수 있고 유연한 컴포넌트를 작성할 수 있다는 부분에서 좋은 기능인 것은 분명하지만, 여러 Context를 중첩해서 사용하다 보면 간단 기능을 담당하는 컴포넌트가 점점 이상하게 변하기 시작한다.

### useContext 사용하기!

```jsx
/** NameContext.jsx */
import { createContext } from "react";

export const NameContext = createContext(null);
```

React Hooks의 useContext를 사용하기 위해 NameContext에 초기값 null을 설정한다.

```jsx
/** App.js */
import logo from './logo.svg';
import './App.css';
import { NameContext } from './context/NameContext';

function App() {
  return (
    <NameContext.Provider value="suy0ng">
      <div className="App">
        <Hello/>
      </div>
    </NameContext.Provider>
  );
}

export default App;
```

NameContexet.Provider 을 이용하여 name에 suy0ng을 전달하였습니다.

```jsx
/** hello.jsx` */
import React, { useContext } from 'react';
import { NameContext } from '../context/NameContext';

function Hello(props) {
    const user = useContext(NameContext);
    return (
        <div>
            {user} 님 안녕하세요!
        </div>
    );
}

export default Hello;
```

useContext의 인수로 NameContext를 받아 user 변수에 저장했습니다. useContext로 전달한 인자는 context 객체 그 자체이어야 합니다.

- 참고자료
    
    [[React] useContext 사용법 및 예제](https://itprogramming119.tistory.com/entry/React-useContext-사용법-및-예제)
    
    [React 강좌) trendy React 3-1. useContext 알아보기](https://velog.io/@public_danuel/trendy-react-usecontext)