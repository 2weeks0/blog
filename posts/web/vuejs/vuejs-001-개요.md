# [Vue.js] 개요

## Vue.js 개요

![vue-logo](/assets/img/thumb/vuejs.png)

프론트엔드 3대장 중 막내라고 불리운다. (첫째는 `Angular`, 둘째는 `React`라고 한다.) `Angular`를 개발한 분이 개인 프로젝트로 개발하다 탄생되었다고 한다. `Vue`의 시작이 `Angular`가 너무 무겁다는 문제점에서부터였다고 하니, 다른 프레임워크보다 쉽게 배울 수 있다는 인식이 있다고 한다. (물론 사실일지도?) 따라서, 곳곳에 `Angular`와 사상과 구조가 상당히 담겨있다고 한다.

`Vue`는 `React`와 `Angular`보다 이후에 출시된 프레임워크이기 때문에, 각각의 장점을 많이 갖췄다. 역시 가상 DOM(Virtual Document Object Model)과 컴포넌트 개념을 흡수해 재사용성을 높였다. 돔이란 웹 페이지를 이루는 태그들을 트리 구조로 만든 객체 모델을 뜻한다. 즉, 브라우저는 DOM을 바탕으로 렌더링을 한다. 

![dom-tree](/assets/img/posts/vuejs/dom-tree.png)

가상 DOM이 등장하게 된 배경은 DOM에 변화가 생겼을 때, 변화된 DOM 트리를 구성하고, 이를 다시 렌더링하는 과정에서 낭비가 발생하기 때문이다. 이 낭비를 줄이기 위해 가상 DOM을 먼저 생성하고, 변화가 생겼을 때, 변화된 요소에만 변화가 적용된 가상 DOM을 전달해 렌더링 한다. 즉, 변경이 일어난 부분만 재렌더링을 한다.

이를 MVVM 패턴, 데이터 바인딩을 통해 구현한다. 잠시 MVVM 패턴에 대해 소개하자면, 기존 MVC 패턴에서는 화면의 변화, 즉 데이터의 변화가 발생할 경우 Controller에서 Model에 데이터 갱신과 화면 갱신을 모두 신경써줘야 했다. 하지만 MVVM 패턴에선 ViewModel이 View와 Model 사이에서 데이터를 화면과 바인딩시켜 관찰한다. 이 때, 데이터가 변경되면 ViewModel이 알아서 화면도 갱신시켜준다. 

또 다른 `Vue`의 특징으로는 HTML 기반의 템플릿을 사용해 러닝 커브가 적다는 것이다. 아마 이 때문에 `Vue`가 다른 프레임워크에 비해 쉽다고 느껴지는 것 같다.`Vue`는 양방향 데이터 바인딩도 지원한다. 물론, 단방향 바인딩이 주가 되지만, 특수한 곳에 양방향 바인딩을 지원한다.

참고로, 필자는 Vue 2를 학습하고 있다.

## 맛 보기 - Hello World

그럼 `Vue`를 통해 HelloWorld 앱을 만들어보자. 먼저, CDN 방식으로 `Vue`를 설치해주자.

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

```html
<body>
    <div id="app">{{ message }}</div>
    <script>
      new Vue({
        el: "#app",
        data: {
          message: "Hello World",
        },
      });
    </script>
</body>
```

위 코드가 `Vue`로 짠 Hello World 앱이다. `Vue` 인스턴스에 el 속성으로 적용될 요소를 지정해주고, data에 message를 추가해줬다. 이를 화면에 출력한 것이다. 여기서 주목할 점은 message의 변화가 곧 화면의 변화로 이어진다는 것이다. message를 변경하기 위해 input 태그를 추가해보자.

```html
<body>
    <div id="app">
      <div>{{ message }}</div>
      <input v-model="message" />
    </div>
    
    <script>
      new Vue({
        el: "#app",
        data: {
          message: "Hello World",
        },
      });
    </script>
</body>
```

`v-model`은 양방향 데이터 바인딩을 뜻한다. 즉, message가 바뀌거나 input 태그의 value가 바뀌면 서로 동기화를 한다는 뜻이다. 이런 데이터 바인딩을 통해 선언형 프로그래밍이 가능해지고, 코드의 가독성과 재사용성, 유지보수성이 크게 향상될 수 있다.