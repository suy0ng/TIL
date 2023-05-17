# Enum(이넘)

### enum의 개념

enum은 열거형 타입을 앞 글자를 따와서 만들어진 단어이다.

enum의 대표적인 예로는 boolean Type이 있다. 

JS에서는 숫자 1 은 True 0은 False에 대응된다, 일종의 Built-in enum이다.

```tsx
enum booleanType {    False = 0,    True = 1}
```

위 코드는 TS의 코드이고 JS로 변환하면 다음과 같이 나타난다.

```tsx
"use strict";
var booleanType;
(function (booleanType) {
    booleanType[booleanType["False"] = 0] = "False";
    booleanType[booleanType["True"] = 1] = "True";
})(booleanType || (booleanType = {}));
```

즉, enum은 JS로 컴파일되는 과정에서 일종의 필요충분조건처럼 Key-Value의 관계가 양방향으로 구현된다.

따라서 콘솔에 찍어보면 다음과 같은 결과를 얻을 수 있다.

### enum의 장점

1. 생산성과 가독성이 높아진다.
2. 정의한 Key-value 관계만 성립할 수 있기 때문에 예기치 못한 에러를 방지할 수 있다.

### enum의 단점

1. 컴파일시 코드의 양 증가
2. Tree-shaking이 되지 않는다.