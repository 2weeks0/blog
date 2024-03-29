# [Next.js] Navigation between pages

## Next.js의 페이지

`pages` -> Next.js에서 페이지는 디렉토리의 파일의 구성 요소다.

페이지는 파일 경로와 url이 매핑된다.

- `pages/index.js` 파일 경로와 `/` url이 매핑된다.
- `pages/posts/first-post.js` 파일 경로와 `/posts/first-post` url이 매핑된다.

## 새 페이지 만들기

`pages/posts/first-post.js` 경로에 파일을 만들어보자.

```javascript
export default function FirstPost() {
  return <h1>First Post</h1>;
}
```

이제 개발 서버가 실행하고 http://localhost:3000/posts/first-post로 진입하면 위에서 만든 페이지를 확인할 수 있다.

즉, pages 디렉토리 아래에 JS 파일을 생성하기만 하면 파일의 경로가 URL 경로가 된다.

어떻게 보면 HTML이나 PHP 파일을 사용하여 웹사이트를 구축하는 것과 비슷하다. HTML을 작성하는 대신 JSX를 작성하고 React 구성 요소를 사용한다.

이제, 웹 페이지에서 페이지 이동을 할 수 있도록 새로 추가된 페이지에 대한 링크를 추가해보자.

## 링크 컴포넌트

웹사이트에서 페이지 사이를 연결할 때 <a>HTML 태그를 사용한다.

Next.js에서 LinkComponent `next/link`를 사용하여 페이지를 연결할 수 있다.

## <Link>

```javascript
import Link from 'next/link';

<Link href="/posts/first-post">move to first post</Link>
```

<Link>태그는 <a>태그를 사용하는 것과 매우 유사하다.