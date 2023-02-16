# React JSX

### **정의와 역할**

**JSX**  : A syntax extension to JavaScript( JavaScript + XML / HTML )

**JSX 코드 예시**

```jsx
const element = <h1>Hello, world</h1>;
```

**JSX의 역할**

: 내부적으로 HTML XML 코드을 JavaScript로 변환해줌

**JSX을 사용한 코드**

```jsx
class Hello extends React.Component {
	render() {
		return <div>Hello {this.props.toWhat}</div>;
	}
}

ReactDom.render(
	<Hello toWhat="World" />
	document.getElementById('root')
);
```

**JSX을 사용하지 않은 코드**

```jsx
class Hello extends React.Component {
	render() {
		return React.createElement('div',null,'Hello ${this.props.toWhat);
	}
}

ReactDOM.render(
	React.createElement(Hello, {toWhat : 'World'),null);
	document.getElementById('root')
}
```

두 코드는 동일한역할을 하고 있다

```jsx
// jsx를 사용한 코드
const element = (
	<h1 className="greeting">
		Hello,world
	</h1>
)
// jsx를 사용하지않은 코드
const element = React.createElement(
	'h1',
	{ className : 'greeting'},
	'Hello Wolrd'
)
```

React.createElement()의 결과로 아래와 같은 객체 생성됨

```jsx
const element = {
	type:'h1',
	props: {
		className:'greeting',
		children : 'Hello, world!'
	}
}
```

createElement의 파라미터

```jsx
React.createElement(
	type,
	[props],
	[...children],
)
```

JSX를 사용하면 장점들이 많기 떄문에 편리함!

**JSX의 장점**

- 간결한 코드, 가독성 향상

```jsx
<div> Hello, {name}</div> //JSX 사용함

React.createElement('div',null,`Hello, ${name}`); //JSX 사용안함
```

- 버그를 발견하기 쉬움!
- Injection Attacks 방어

```jsx
const title = response.potentiallyMaliciousInput;

// 이코드는 안전합니다.
const element =<h1>{title}</h1>
```

**JSX의 사용법**

JavaScripts코드 + XML / HTML

```jsx
const name = 'suy0ng';
const element = <h1>안녕, {name}</h1>

ReactDOM.render{
	element,
	document.getElementById('root')
);
```