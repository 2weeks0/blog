## HTML5 웹 문서를 구성하는 3요소

![html5.png](/assets/img/posts/html-001/html5.png)

## Web & HTML 작동 원리

- 서버는 클라이언트의 요청 내용을 분석하여 결과를 HTML로 전송하고, 연결을 끊는다.
- 클라이언트는 서버로부터 전달 받은 HTML을 Web Browser에 표시한다.

![c-b-s](/assets/img/posts/html-001/client-browser-server.png)

## HTML 개요

- Hypertext Markup Language의 약자
- 구조

    ```html
    <!DOCTYPE html> <!-- 문서 type 정의 -->
    <html>
    	<head> <!-- 문서 머리글: 메타 정보 제목, 검색 엔진에서 사용할 키워드, 내용 등등 -->
    		<meta charset="UTF-8">
    		<title>title</title>
    	</head>
    	<body> <!-- 문서 본체 -->
    		body
    	</body>
    </html>
    ```


- 태그와 속성
    - 태그는 시작 태그와 종료 태그로 쌍을 이루거나 시작 태그만 존재한다.
    - 종료 태그엔 / 문자로 구분된다.
    - 또 각 태그에는 속성값이 있다.

        ```html
        <a href="https://2weeks0.tistory.com/">a 태그</a>
        ```

    - 어느 태그에나 들어갈 수 있는 공용 태그가 있다.
        1. class: tag에 적용할 스타일 클래스를 지정
        2. dir: 텍스트 방향 지정 (ltr, rtl)
        3. id: 유일한 id 지정 (주로 자바스크립트에서 id를 통해 태그를 참조함)
        4. style: 인라인 스타일 적용
        5. title: 추가 정보 지정. tag에 마우스 포인터를 위치시킬 때, 해당 title이 뜸.

- head 태그의 요소
    - html 문서의 정보를 전달하는 역할
    - title, meta, style, script, link 태그 포함 가능
- body 태그의 요소
    - Web Browser에 보여질 문서 내용을 작성하는 곳!
    - head 태그 하단에 위치함
    
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8"> <!-- 인코딩 방식 -->
        <title>title</title> <!-- title -->
        <meta name="author" content="author"> <!-- 제작자 -->
        <meta name="description" content="description"> <!-- 설명, 검색 엔진이 수집 -->
        <meta name="keyword" content="keyword1, keyword2"> <!-- 키워드, 컴마로 구분하여 나열, 검색 엔진이 수집 -->
        <script type="text/javascript"></script>
        <style type="text/css">
        .common {
          background-color: steelblue;
          color: white;
        }
        #private {
          background-color: magenta;
        }
      </style>
        <link rel="stylesheet" href="test.css">
    </head>
        <body>
        <h3>문단의 제목이 들어간다.</h3>
        <div class="common">div 1(.common)</div>
        <div class="common">div 2(.common)</div>
        <div class="common">div 3(.common)</div>
        <div class="common">div 4(.common)</div>
    
        <div id="private">div 5(#private)</div>
      </body>
    </html>
    ```