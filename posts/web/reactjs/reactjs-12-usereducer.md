# [React.js] useReducer

## `useReducer`란?

`useReducer`는 `useState`를 대체하는 훅이다. `Redux`에서 사용하는 방식과 매우 유사하다. `reducer`에 `action`에 따른 메소드를 정의해두고, `dispatch`로 상태를 변경시켜 사용한다.

## 예제

먼저, `useState`로 구현한 Counter 예제의 소스다.

```javascript
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    const increment = () => {
        setCount(prev => prev + 1);
    }

    const decrement = () => {
        setCount(prev => prev - 1);
    }

    return (
        <div>
            <p>count: {count}</p>
            <button onClick={increment}>+1</button>
            <button onClick={decrement}>-1</button>
        </div>
    );
}
```

이를 `useReducer`로 변경하면 아래와 같이 쓸 수 있다.

```javascript
import { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return {count: state.count + 1};
    case "decrement":
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
    const [state, dispatch] = useReducer(reducer, {count: 0});

    return (
        <div>
            <p>count: {state.count}</p>
            <button onClick={() => dispatch({type: "increment"})}>+1</button>
            <button onClick={() => dispatch({type: "decrement"})}>-1</button>
        </div>
    );
}
```

기존 Counter 컴포넌트에는 increment, decrement의 로직이 컴포넌트 안에 있었지만, `useReducer`를 사용함으로써 그 로직을 컴포넌트 밖으로 분리할 수 있다는 장점이 있다.