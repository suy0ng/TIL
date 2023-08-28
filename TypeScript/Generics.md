# Generic(제너릭)
제너릭(Generics)은 타입스크립트에서 함수, 클래스, interface, type alias를 사용하게 될때 여러 종류의 타입에 대하여 호환을 맞춰야 하는 상황에서 사용하는 문법입니다.

A와 B를 받아와서 합치는 함수 merge를 만들어 보겠습니다.

```tsx
function merge< A ,B >(a:A, b:B) : A & B {
	return {
		...a,
		...b
	}; 
}

const merged = merge({foo:1},{bar:1})
```

이렇게 함수에서 Generic를 사용하면 다양한 타입을 넣을 수 도 있고 타입 지원으 지켜낼 수 있습니다.

이번에는 타입에서 Generic를 사용해보겠습니다. 

```tsx
type Items<T> = {
	list = T[];
}
```

이렇게 하면 타입에서도 Generic를 사용할수 있습니다.
