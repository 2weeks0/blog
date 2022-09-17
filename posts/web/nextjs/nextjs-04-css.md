# [Next.js] Css

Next js 에서 css 파일을 적용하기 위한 방법은 2가지가 있다.

1. global: `styles/global.css` 
2. module: `styles/name.module.css` (반드시 `.module.css`로 끝나야 함)

Css module은 지역적으로 컴포넌트 내에 css 속성을 적용할 수 있다.

사용법은 아래와 같다.

먼저 `styles/Example.module.css` Css 파일을 생성한다. 

```css
.container {
    max-width: 36rem;
    padding: 0 1 rem;
    margin: 3rem auto;
}
```

그 후, 위 css 파일을 적용시킬 컴포넌트를 만든다.

```javascript
import styles from './example.module.css';

export default function Example({ children }) {
  return <div className={styles.container}>Example</div>;
}
```

위와 같이 css 파일을 생성하고 적용하면 Next js에서 알아서 겹치지 않는 class 이름은 만들어 준다.