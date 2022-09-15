# [Next.js] Assets, Metadata

## Assets

Next.js는 `public` 디렉토리 하에서 `pages`로 라우팅을 하는 것처럼 static assets을 제공할 수 있다. 

`public/images` 디렉토리 아래에 이미지 파일을 위치시키면 정적 자원으로 사용할 수 있다.

```javascript
<img src="/images/name.jpg" />
```

위처럼 HTML <img> 태그를 사용하면 최적화되지 않은 이미지를 렌더링할 수 있다.

하지만 Next.js는 최적화된 이미지 컴포넌트인 `next/image` <Image> 태그를 제공한다.

최적화된 이미지 컴포넌트란 빌드 시 이미지를 최적화하는 대신 사용자가 요청할 때 이미지를 최적화시킨다. 따라서 웹 페이지가 이미지 파일을 몇개를 갖고 있던지 상관 없이 빌드 시간을 단축시킬 수 있다.

또한, 이미지는 lazy load 되기 때문에 스크롤되어 viewport에 진입했을 때 로드되고 이는 화면 밖 이미지를 로드시키지 않기 때문에 성능이 뛰어나다.

`next/image` <Image> 태그의 예는 아래와 같다.

```javascript
import Image from 'next/image';

const ImageComponent = () => (
  <Image
    src="/images/name.jpg" 
    height={144}
    width={144}
    alt="name"
  />
);
```

## Metadata

metadata는 Next.js에서 제공하는 `next/head` <Head> 태그를 사용하여 작성할 수 있다.

```javascript
import Head from 'next/head';

<Head>
  <title>Create Next App</title>
  <link rel="icon" href="/favicon.ico" />
</Head>
```

## Third-Patry JavaScript

Next.js의 `next/script` <Script> 태그는 HTML <script> 태그의 최적화 및 추가 기능이 포함된 태그다.

```javascript
import Script from 'next/script';

<Script
  src="https://connect.facebook.net/en_US/sdk.js"
  strategy="lazyOnload"
  onLoad={() =>
    console.log(`script loaded correctly, window.FB has been populated`)
  }
/>
```
<Script> 태그는 아래와 같은 추가 기능을 갖고 있다.

1. `strategy` - 스크립트가 load 되는 타이밍을 컨트롤하는 option이다. 예제의 `lazyOnload`는 브라우저의 idle time 때, 느즈막히 로드한다는 뜻이다.
2. `onLoad` - 스크립트가 로드될 때, 실행되는 callback 함수다.