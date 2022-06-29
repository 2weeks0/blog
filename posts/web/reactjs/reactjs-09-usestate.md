# [React.js] useState

## `useState`란?

`useState`는 `state`를 함수형 컴포넌트에서도 사용할 수 있게 만들어주는 특별한 함수다. 기존엔 `state` 를 사용하기 위해선 클래스 컴포넌트를 사용해야만 했는데, React 16.8 버전부터 Hook이 추가되어 함수형 컴포넌트에서도 사용할 수 있게 되었다.

사용법은 아래와 같다.

```javascript
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>count: {count}</p>
            <button onClick={() => setCount(count + 1)}>+1</button>
        </div>
    );
}
```

## `useState`의 반환값

```javascript
const [count, setScount] = useState(0);
```

위 예제에서 `useState`의 반환값을 `[count, setCount]`로 받고 있는데, 이는 JavaScript의 배열구조분해 문법을 통해 `state` 변수와 `setState` 함수를 받는 것과 유사하다.

## `useState`의 인자값

`useState`의 인자로 `state` 초기값을 넘겨주면 된다. 위 예제에선 `useState(0)`으로 주어 number형 count에 초기값 0으로 세팅해준 것이다. 
> 여러 `state`가 필요할 땐, 의미에 따라 객체로 묶어 여러 `useState` 구문을 사용할 수도 있다.

## `state` 가져오기

`useState`로 받아온 첫번째 인자값의 변수로 사용할 수 있다.

```javascript
<p>count: {count}</p>
```

## 'state' 갱신하기

`useState`로 받아온 두번째 인자값의 변수로 사용할 수 있다.

```javascript
<button onClick={() => setCount(count + 1)}>+1</button>
```