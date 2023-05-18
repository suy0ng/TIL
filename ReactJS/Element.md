# Element

**Element란?**

리액트 앱을 구성하는 가장 작은 블록들

 

**DOM:**

화면에 나타나는 내용을 기술하는 자바스크립트 객체 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/995c051d-2423-4e3f-9681-8f98104d1108/Untitled.png)

결국 React Element는 Dom Element의 가상의 Element이다

Elements는 화면에서 보이는 기술

```jsx
const element = <h1>Hello, World!</h1>
```

리액트 Elements는 자바스크립트 객체 형태로 존재한다. 이 객체는 불변성을 가지고 있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/32220365-9de1-4ea2-a783-29328f1624fc/Untitled.png)

다음과 같은 형태로 변할것이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1af31ae-72d3-4e95-b777-8445f39c96ab/Untitled.png)

리엑트의 element는 우리눈에 보이는대로 구성된다.

**Elements의 특징**

**불변성( : 변할수없는 성질)**

Element 생성후에는 children이나 attributes를 바꿀 수 없다!

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d2b0849f-e4fb-4fee-8342-a682cc380d99/Untitled.png)

붕어빵처럼 내부의 내용을 바꿀수 없다고 생각하면된다.

화면에 변화를 주기위해서는 새로운 element를 생성해서 바꿔치기 하면된다,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87411ddb-00cd-41af-b85e-5ef649e6faa5/Untitled.png)

Elements 렌더링하기

```jsx
<div id='root'></div>
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/432269b8-04e2-442d-a964-f4aa887b45bd/Untitled.png)

루트에 렌더링하기위해서 쓰는 코드

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f28ef99d-00d0-4538-a62b-76c2a90de2ef/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e89291a-4c37-42d5-878c-acb571d8c184/Untitled.png)

이코드는 새로운 Elements를 생성하여 기존 Element와 바꿔치기하는 코드이다