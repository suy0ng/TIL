# TypeAlias사용하기

`type`은 특정 타입에 별칠을 붙이는 용도로 사용한다.

```tsx
type Person = {
	name : string;
	age? : number;
}

type Job = Person & {
	job : string;
}

const person : Person = {
	name : '홍길동';
}

const jobPerson : Job = {
	name: '홍길동';
	job : '무직';
}
```