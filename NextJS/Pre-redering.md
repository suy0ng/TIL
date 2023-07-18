# Pre-rendering

기본적으로 Next.js는 모든 페이지를 사전 렌더링합니다. 즉, Next.js는 클라이언트측 자바스크립트에서 모든 작업을 수행하는 대신 미리 각 페이지에 대한 HTML을 생성합니다. 사전 렌더링은 더 나은 성능과 SEO를 가져올 수 있다.

생성된 각 HTML은 해당 페이지에 필요한 최소한의 자바스크립트코드와 열결됩니다. 페이지가 브라우저에 의해 로드되면 해당 자바스크립트 코드가 실행되어 페이지가 상호작용하도록 합니다. 이 과정을 Hydration이라고 합니다.

### Pre-rendering의 두 가지 형태

Next.js에서는 Static Generation 와 SSR(Server-side Rendering)방법 두가지가 있습니다. 이 두가지의 차이는 HTML을 생성할때 발생합니다.

#### Static Generation

Static Generation은 빌드시 HTML을 생성하는 사전 렌더링 방법이다. 미리 렌더링된 HTML이 각 요청에서 다시 사용 된다.
![img](https://nextjs.org/static/images/learn/data-fetching/static-generation.png)


#### Server-side Rendering

Server-side rendering은 각 요청마다 HTML을 생성하는 하는 방법이다.
주로 페이지가 자주 업데이트 되는 페이지에 사용한다.
![img](https://nextjs.org/static/images/learn/data-fetching/server-side-rendering.png)

