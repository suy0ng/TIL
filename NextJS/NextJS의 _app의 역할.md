# Next.js의 \_app의 역할

### \_app.js 의 역할

\_app.js를 사용하는 주요 목적으로는 공통으로 적용할 속성을 관리하기 위해서 사용합니다.

```js
export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```
