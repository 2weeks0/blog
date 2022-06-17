# [React.js] 개요

React.js 라이브러리를 공부하며 글을 남겨볼 생각이다. 공식 문서(https://ko.reactjs.org/)를 참고하며 하나하나 기록하며 공부하는 것이 목표이다. React에 관한 첫 글인 만큼 본 글에선 React의 몇 가지 특징에 대해 알아볼 것이다.

## 1. 선언형 프로그래밍

클라이언트 프로그래밍 방식에는 명령형이 있고, 선언형이 있다. React.js, Vue.js 등 비교적 최신 프레임워크 내지 라이브러리는 선언형 프로그래밍 방식을 따르고, JQuery 는 명령형 프로그래밍 방식이다. 둘의 차이를 카운터 앱을 예로 들어 비교해보자. 명령형 프로그래밍으로 짠 카운터 앱에선 버튼을 클릭할 때마다 count 값을 읽어와서 +1한 값을 해당 뷰에 다시금 써주어야했다. 하지만 선언형 프로그래밍 방식에선 count 값을 data로 갖고 있고, 뷰는 해당 data의 값을 보여주기만 한다. 이 때, 버튼을 클릭하게 되면 data 값을 +1 해주고, 뷰는 data의 변화를 감지해서 변화된 data를 표시한다. 데이터가 주체가 되어 화면을 구성하는 것이다.

선언형 프로그래밍의 장점은 많다. 명령형 프로그래밍 방식보다 훨씬 간결한 코드를 작성할 수 있고, 코드의 흐름을 예측하기가 쉽다. 이는 디버그는 물론이고 유지보수에 상당한 이점이 있기 때문에 선호된다.

## 2. 재활용이 가능한 컴포넌트

React의 개념 중 State라는 것이 있는데, 이는 앞서 말한 선언형 프로그래밍 방식의 data를 말한다. 하나의 컴포넌트는 하나의 state를 갖고, state가 변화할 때마다 해당 컴포넌트 뷰를 갱신한다. 즉, 직접적으로 DOM을 컨트롤하지 않아도 화면을 관리할 수 있고, 이는 JavaScript 위에서만 동작하기 때문에 가볍게 처리할 수 있다. 또, 이렇게 캡슐화된 컴포넌트는 재활용하기에 적합하다.

또, React에선 class로 컴포넌트화시키는데, 안드로이드로 개발을 처음 배운 필자로썬 매우 익숙한 방식이다. 이 때문인지 Vue보다 더 정이 가는 것 같다.

## 3. 유연한 라이브러리/프레임워크를 사용

흔히 웹 프레임워크 3대장을 React, Vue, Angular라고 한다. Angular는 아직 접해보지 않아 모르겠고, Vue는 확실히 프레임워크라고 느껴졌다. 하지만 React는 프레임워크라고 보긴 어려울 것 같고 라이브러리에 더 가까운 것 같다. 실제로 React 공식 홈페이지에서 라이브러리라고 명명하고 있다. (Vue는 프레임워크라고 칭함) 순수 JavaScript의 class로 컴포넌트를 구성하기 때문에 타 JavaScript 라이브러리 내지 프레임워크의 이식이 수월하다. 아직 본격적으로 React의 맛을 못보았기 때문에, 이 부분에서 느낀 점은 없지만 Vue로 작업해보면서 다른 JavaScript 라이브러리 사용이 매우 불편함을 느꼈기 때문에 React에 많은 기대를 하고 있다.

## 4. JSX

React에선 JSX라는 특이한 문법이 등장한다. React의 컴포넌트 class는 `render()`라는 메소드를 구현하여 뷰를 작성한다. 이 때, JSX 문법이 등장한다.

```javascript
class HelloMessage extends React.Component {
  render() {
    return (
      <h1>
        Hello {this.props.name}
      </h1>
    );
  }
}

ReactDOM.render(
  <HelloMessage name="홍길동" />,
  document.getElementById('root')
);
```
위 컴포넌트는 `<h1>` 태그안에 `Hello 홍길동`이라는 문자열을 갖는 컴포넌트다. 앞서 말한 `render()` 함수에 JSX 문법으로 HTML 태그를 구성해 반환해주면 된다. 위 JSX 문법은 `Babel`에 의해 아래와 같이 컴파일된다.

>`Babel`이란?  
>Babel is a JavaScript compiler.  
>공식 홈페이지의 소개에 의하면 JavaScript 컴파일러라고 한다. 현재 TypeScript를 필두로 많은 스크립트 언어가 사용되고 있다. 여러 스크립트 언어들이 JavaScript로 컴파일되어야 하는데, 이를 담당하는 것이 바로 Babel이다.  
>또, 언어의 버전이 다양한데, 구식 브라우저나 구버전 브라우저에서는 해당 버전이 지원되지 않을 수 있다. 이 때, Babel이 브라우저가 해석 가능한 버전의 언어로 변환해준다.

```javascript
class HelloMessage extends React.Component {
  render() {
    return React.createElement("h1", null, "Hello ", this.props.name);
  }
}

ReactDOM.render(React.createElement(HelloMessage, {
  name: "홍길동"
}), document.getElementById('root'));
```

즉, JSX는 `React.createElement()` 메소드를 좀 더 가독성있게 작성할 수 있도록 도와주기 위한 문법이다.