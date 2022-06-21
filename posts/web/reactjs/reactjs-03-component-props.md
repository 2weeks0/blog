# [React.js] Component와 Props

컴포넌트와 Props의 개념은 간단하다. 컴포넌트란 재사용 가능한 UI를 말하고, Props는 컴포넌트를 생성할 때, data를 넘겨주는 것을 말한다.
React에서 컴포넌트를 생성하는 방법은 2가지다.

## 컴포넌트 생성 방식

### 함수 컴포넌트

```javascript
function HelloWorld(props) {
    return <h1>Hello {props.name}</h1>;
}
```

위처럼 함수에 JSX 문법을 사용한 UI를 return 해주면 함수형 컴포넌트를 생성할 수 있다. 이 때, 주의해야할 것은 함수 이름의 첫글자가 대문자여야 한다는 것이다. 대문자로 정해야 JSX 문법에서 컴포넌트 타입으로 인식할 수 있다.


### 클래스 컴포넌트

```javascript
class HelloWorld extends React.Component {
    render() {
        return <h1>Hello {this.props.name}</h1>;
    }
}
```
클래스 컴포넌트는 `React.Component` 클래스를 상속하여 만들 수 있다. 이 또한 대문자로 시작해야 한다.


## 컴포넌트 렌더링

이제 앞에서 만든 컴포넌트를 사용해보자.

```javascript
const element = <HelloWorld name="홍길동"/>
```

일반 HTML 태그처럼 사용할 수 있지만, 대문자로 시작해야한다. (대문자가 아니면 내장 태그로 인식해 불러올 수 없다.) 이게 앞서 언급한 컴포넌트의 이름이 대문자로 시작해야하는 이유다.


## Props는 Read-Only

React에서 data는 위에서 아래로 흘러야 한다. 즉, 부모에서 자식으로 흘러야 한다. 부모가 자식에게 준 data를 자식은 변경할 수 없어야 한다. 일관된 data 흐름을 유지해야 가독성 있는 코드를 작성할 수 있다.

이러한 규칙에 의거해 props도 읽기 전용으로써, 자식이 변경해서는 안된다. 즉, JavaScript의 `순수 함수`처럼 동작해야 한다.

> 순수 함수란?  
> 인자 값을 변경하지 않는 함수

data의 변화를 위해선 `state`를 활용해야 한다. `state`는 다음 장에서 확인해보자! 