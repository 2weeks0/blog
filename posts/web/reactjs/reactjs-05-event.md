# [React.js] event

React에서 이벤트를 처리하는 방법에 대해 알아보자. HTML에서 처리하는 방식과 유사하나 2가지 규칙이 있다.

1. React의 이벤트는 소문자가 아닌 카멜 케이스(camelCase)를 사용한다.
2. JSX를 이용하여 이벤트 핸들러를 넘긴다.

```javascript
<button onClick={handleClick}>Button</button>
```

폼에서 기존 이벤트를 제거하기 위해 `preventDefault()`를 사용하려면 아래와 같이 해주면 된다.

```javascript
function Form() {
    function handleSubmit(e) {
        e.preventDefault();
        console.log("clicked!!");
    }

    return (
        <form onSubmit={handleSubmit}>
            <button type="submit">Submit</button>
        </form>
    );
}
```

클래스형 컴포넌트로 작성하면 아래와 같다.

```javascript
class MyButton extends React.Component {
    constructor(props) {
        super(props);
    }

    handleSubmit(e) {
        e.preventDefault();
        console.log("clicked!!");
    }

    render() {
        return (
            <form onSubmit={this.handleSubmit}>
                <button type="submit">Submit</button>
            </form>
        );
    }
}
```


## Handler Bind

만약 handler 메소드에서 클래스 컴포넌트의 `this`를 사용해야 한다면, `constructor()`에서 handler 메소드를 바인드해줘야 한다. JavaScript 클래스 메소드는 기본적으로 `this`가 바인드되지 않아, 그냥 사용하면 `this`가 `undefined`를 가리킨다.

```javascript
class MyButton2 extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            isOn: false,
        };

        this.handleClick = this.handleClick.bind(this); // 바인드해주지 않으면 handleClick에서 this.setState를 쓸 수 없음!!!
    }

    handleClick() {
        this.setState(prevState => ({
            isOn: !prevState.isOn,
        }));
    }

    render() {
        return (
            <button onClick={this.handleClick}>isOn: {this.state.isOn ? "ON" : "OFF"}</button>
        );
    }
}
```

