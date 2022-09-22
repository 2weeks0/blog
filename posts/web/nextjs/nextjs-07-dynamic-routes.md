# [Next.js] Dynamic Routes

## Page Path Depends on External Data

동적 라우트란 외부 데이터에 의해 path가 정해져야할 때 사용한다. Next.js는 외부 데이터에 의한 path를 통해 페이지를 정적으로 생성하는 방식을 지원한다. 즉, 동적 URL을 가질 수 있다.

![](../../../assets/img/posts/web/nextjs/07-01.png)


## How to Statically Generate Pages with Dynamic Routes

한 가지 예로 블로그를 생각해보자.

만약 URL이 `/posts/[id]` 형식으로 되어있다면 `dynamic-routes.md` 파일이 `/posts/dynamic-routes` 와 같이 위치해야 한다.

이를 Next.js에서는 `/pages/posts/[id].js` 의 파일 경로를 잡아주면 된다.

```javascript
import Layout from '../../components/layout';

export default function Post() {
  return <Layout>...</Layout>;
}

export async function getStaticPaths() {
  // Return a list of possible value for id
}

export async function getStaticProps({ params }) {
  // Fetch necessary data for the blog post using params.id
}
```

`getStaticPaths` 함수는 `Static Generation` 방식으로 생성할 `[id]` 값을 알려줄 때, 사용한다.

`getStaticProps` 함수에서 `params`란 dynamic Routes를 위해 받은 `[id]`값을 담고 있는 변수다.

![](../../../assets/img/posts/web/nextjs/07-02.png)


## implement `getStaticPaths`

`getStaticPaths` 함수를 구현하여 Dynamic Routes를 `Static Generation` 방식으로 pre-rendering 해보자

만약, Dynamic Routes의 경로가 `/posts/[id]`와 같고, id에 1 이상의 정수가 들어온다고 가정하자. 그리고 `Static Generation`할 id가 1~3라고 해보자.

위 경우엔 `getStaticPaths` 함수를 아래와 같이 작성하면 된다.

```javascript
export async function getStaticPaths() {
  return {
    [
      {
        params: {
          id: 1,
        },
      },
      {
        params: {
          id: 2,
        },
      },
      {
        params: {
          id: 3,
        },
      },
    ],
    fallback: false,
  }
}
```

## fallback

`getStaticPaths` 함수로 반환하는 객체엔 `fallback` 옵션을 줄 수 있다.

`fallback`엔  `false` | `true` | `"blocking"` 3가지 옵션을 줄 수 있다. 그럼 의미를 살펴보자.

### fallback: false

`getStaticPaths`로 반환하지 않은 페이지는 모두 404로 보내진다. 위 예제에선 id 값에 1~3을 제외한 다른 값이 오면 404 페이지로 연결된다.

### fallback: true

`getStaticPaths`로 반환하지 않은 페이지에 접속 시, 해당 페이지가 `Static Generation` 방식으로 HTML 페이지가 생성된다. 원래 `Static Generation` 방식은 build time에 HTML 페이지를 만들지만, Dynamic Routes 페이지가 많을 경우 build time을 줄이기 위해 위 옵션을 줄 수 있다.

즉, fallback이 true일 경우, `getStaticPaths`로 반환하지 않은 페이지에 처음 접속한 사용자는 접속 시간이 오래 걸릴 지 몰라도, 그 이후 해당 페이지에 접속하는 사용자는 즉각적으로 페이지를 확인할 수 있다.

### fallback: "blocking"

`getStaticPaths`로 반환하지 않은 페이지에 접속 시, `Server-side Rendering` 방식으로 rendering 된 페이지를 보여준다.