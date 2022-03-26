# [HTML] form

## form이란?
- 사용자로부터 데이터를 입력 받아 서버에 전송하기 위한 용도로 사용
- 사용자가 입력한 요소들 모두 \<form\> 태그 하위에 위치해야 서버로 전송됨.

|tag명|설명|
|:---:|:---|
|\<form\>|사용자에게 입력 받을 항목을 정의. form tag 내부에 여러 개의 요소롤 포함|
|\<input\>|텍스트, 체크 박스, 라디오 버튼 등 데이터를 입력받을 수 있음|
|\<textarea\>|여러 줄의 문자 입력|
|\<button\>|버튼|
|\<select\>|select box|
|\<optgroup\>|select 박스 내에 그룹|
|\<option\>|select 박스 내의 아이템|
|\<label\>|input 태그에 라벨링을 할 수 있음. 이 라벨 태그를 클릭 시, 해당 input 태그에 포커스가 감|
|\<fieldset\>|입력 항목을 그룹화|
|\<legend\>|fieldset의 이름을 설정|

### form 태그 옵션
- 사용자가 입력한 데이터를 어떤 방식으로 서버에 전달할 지 등을 결정.

|속성|설명|
|:---:|:---|
|method(GET)|주소에 사용자가 입력한 내용이 표시. 256 ~ 2048bytes 길이 제한|
|method(POST)|HTTP 메세지의 body에 담아서 전송. 길이 제한이 없고, 입력 내용이 표시되지 않음|
|action|서버 상의 프로그램(URL) 지정|

### 예제 1 - 로그인
```html
<div>
    <h2>로그인</h2>
    <form method="post" action="login">
        <fieldset>
            <legend>필수 입력 항목</legend>
            <ul type="none">
                <li>
                    <label for="id">아이디: </label>
                    <input type="text" id="id" name="id">
                </li>
                <li>
                    <label for="pw">비밀번호: </label>
                    <input type="password" id="pw" name="pw">
                </li>

            </ul>
        </fieldset>
        <fieldset>
            <legend>선택 입력 항목</legend>
            <ul type="none">
                <li>
                    <label for="address">주소: </label>
                    <input type="text" id="address" name="address">
                </li>
                <li>
                    <label for="phone">핸드폰 번호: </label>
                    <input type="tel" id="phone" name="phone">
                </li>
            </ul>
        </fieldset>
        <input type="submit" value="로그인">
    </form>
</div>
```
![예제1](/assets/img/posts/html-005/ex01.jpg)

### input 태그 옵션 - type
- type에 따라 UI가 바뀜. 특히 모바일 환경에서는 키보드 layout도 바뀜.

|type명|설명|
|:---:|:---|
|text|한 줄짜리 텍스트|
|password|비밀번호, *로 표시|
|search|검색|
|tel|전화번호|
|url|url 주소|
|email|email 주소|
|datetime|UTC 기준 날짜와 시간|
|datetime-local|Local 기준 설정된 날짜와 시간|
|date|local 기준 날짜|
|time|local 기준 시간|
|number|숫자|
|range|숫자를 조절할 수 있는 슬라이드 막대|
|color|색깔표|
|checkbox|다중 선택이 가능한 체크 박스|
|radio|단일 선택의 라디오 버튼|
|file|파일 첨부|
|submit|전송 버튼|
|reset|리셋 버튼|
|hidden|UI가 없지만, 서버로 값을 보낼 때 사용|

### 예제 2 - 여러 input
```html
<div>
    <form>
        <ul type="none">
            <li>
                <label for="search">검색: </label>
                <input type="search" id="search" name="search">
            </li>
            <li>
                <label for="url">url: </label>
                <input type="url" id="url" name="url">
            </li>
            <li>
                <label for="email">email: </label>
                <input type="email" id="email" name="email">
            </li>
            <li>
                <label for="number">number: </label>
                <input type="number" id="number" name="number">
            </li>
            <li>
                <label for="range">range: </label>
                <input type="range" id="range" name="range">
            </li>
            <li>
                <h5>좋아하는 과일을 고르세요</h5>
                <label><input type="checkbox" name="fruit" value="사과">사과</label>
                <label><input type="checkbox" name="fruit" value="바나나">바나나</label>
                <label><input type="checkbox" name="fruit" value="복숭아">복숭아</label>
                <label><input type="checkbox" name="fruit" value="배">배</label>
            </li>
            <li>
                <h5>성별을 고르세요</h5>
                <label><input type="radio" name="sex" value="남자">남자</label>
                <label><input type="radio" name="sex" value="여자">여자</label>
            </li>
        </ul>
    </form>
</div>
```

![예제2](/assets/img/posts/html-005/ex02.jpg)