# [React.js] 조건부 렌더링 (Conditional Rendering)

어떤 변수 값에 따라 화면에 렌더링되는 요소가 달라지는 경우가 있다. 예를 들어, 로그인된 상태라면 로그 아웃 버튼을 보여줘야 하고, 그 반대 상태면 로그인 버튼을 보여줘야 한다. 이럴 때, element를 변수로 담아 사용하면 된다.

```javascript
function LoginControl(props) {
  // 생략

  const isLoggedIn = this.state.isLoggedIn;
  let button;
  if (isLoggedIn) {
    button = <LogoutButton onClick={this.handleLogoutClick} />;
  } else {
    button = <LoginButton onClick={this.handleLoginClick} />;
  }

  return <div>{button}</div>;
}
```

따로 변수를 사용하고 싶지 않다면 아래와 같이 쓸 수 있다.

```javascript
function LoginControl(props) {
  // 생략

  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      {isLoggedIn ? (
        <LogoutButton onClick={this.handleLogoutClick} />
      ) : (
        <LoginButton onClick={this.handleLoginClick} />
      )}
    </div>
  );
}
```

JSX 의 중괄호 안에는 표현식을 포함할 수 있기 때문에 위처럼 사용할 수 있다. 가독성을 고려해서 두 방법 중 마음에 드는 방식을 사용하면 된다.


## `null`로 렌더링 막기

위 예제처럼 특정 변수 값에 따라 `ComponentA` 또는 `ComponentB`를 보여줄 수도 있지만, 아예 안보이게 만들고 싶을 떄도 있다. 이 때는 return 값으로 `null`을 반환해주면 된다.

```javascript
function WarningBanner(props) {
  if (!props.warn) {
    return null;
  }

  return (
    <div className="warning">
      Warning!
    </div>
  );
}
```