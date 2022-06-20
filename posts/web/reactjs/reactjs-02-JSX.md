# [React.js] JSX

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

## 표현식

JSX내에서 변수 값을 출력하기 위해선 `{}` 중괄호로 묶어주면 된다.

```javascript
const name = "홍길동";
const element = <h1>Hello, {name}</h1>;
```

중괄호 안에는 JavaScript의 표현식을 넣을 수 있고, `1 + 1`, `foo()` 등 JavaScript의 문법 그대로 사용하면 된다.

innerHTML 뿐만 아니라 속성을 적용할 때도 동일하게 사용할 수 있다.

```javascript
const element1 = <a href="https://www.reactjs.org"> link </a>;

const url = "https://www.reactjs.org";
const element2 = <a href={url}> link </a>;
```

## 단일 노드

JSX 내엔 하나의 부모 노드로 감싼 형태의 구조만 허용된다.

```javascript
const element1 = <h1>Hello</h1><h1>Hi</h1>; // X
const element2 = <div><h1>Hello</h1><h1>Hi</h1></div>; // O
```

## 점 표기법 사용

JSX 내에서도 점 표기법을 사용하여 변수에 접근할 수 있다.

```javascript
import React from 'react';

const MyComponents = {
  DatePicker: function DatePicker(props) {
    return <div>Imagine a {props.color} datepicker here.</div>;
  }
}

function BlueDatePicker() {
  return <MyComponents.DatePicker color="blue" />;
}
```


## 컴포넌트는 대문자로 시작

Element가 소문자로 시작하는 건 `div` 등의 내장 컴포넌트를 뜻하며, 커스텀으로 만든 컴포넌트는 대문자로 시작해야 한다.

```javascript
import React from 'react';

// 잘못된 사용법 -> 컴포넌트이므로 Hello여야 함!! (대문자로 시작)
function hello(props) {
  return <div>Hello {props.toWhat}</div>;
}

function HelloWorld() {
  return <hello toWhat="World" />; // 잘못된 사용법
}
```

컴포넌트 함수는 대문자로 시작해야 하고, JSX 문법 내에서 사용할 떄, 대문자로 시작되어야 한다. 따라서 위 코드를 수정하면 아래와 같다.

```javascript
import React from 'react';

// 잘못된 사용법 -> 컴포넌트이므로 Hello여야 함!! (대문자로 시작)
function Hello(props) {
  return <div>Hello {props.toWhat}</div>;
}

function HelloWorld() {
  return <Hello toWhat="World" />; // 잘못된 사용법
}
```

## 변수 내 컴포넌트 사용

Element 타입에 JavaScript에서 사용하는 표현식을 거진 사용할 수 없다. 따라서 객체 내의 변수를 Element 타입으로 사용해야할 경우, 그 값을 대문자 변수에 할당시켜서 사용하면 된다.

```javascript
import React from 'react';
import { PhotoStory, VideoStory } from './stories';

const components = {
  photo: PhotoStory,
  video: VideoStory
};

function Story(props) {
//   return <components[props.storyType] story={props.story} />; // 잘못된 사용법

    const SpecificStory = components[props.storyType];
    return <SpecificStory story={props.story} />; // 올바른 사용법
}
```