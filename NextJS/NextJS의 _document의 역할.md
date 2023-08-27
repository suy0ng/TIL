# Next.js의 \_document.js의 역할

\_document.js 파일은 사용자가 페이지를 렌더링 할때 사용되는 <head>, <body>를 커스텀할때 사용됩니다.

```js
import { Html, Head, Main, NextScript } from 'next/document'

export default function Document() {
  return (
    <Html>
      <Head />
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  )
}
```

반드시 _document를 작성할때는 HTML, Head, Main, NextScript 를 작성해야합니다. 그리고
_document를 작성할때 `_document`에서만 렌더링 되므로 onClick같은 이벤트 처리를 할 수 없습니다.


