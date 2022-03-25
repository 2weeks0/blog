## Table

- HTML table 모델은 데이터를 행과 열의 셀(cell)에 표시
- table에 셀(cell)엔 다른 태그가 들어갈 수 있음
- 행 그룹 요소인 \<thead\>, \<tbody\>, \<tfoot\>으로 나눌 수 있음
- table의 셀(cell)은 머리글(\<th\>)와 데이터(\<td\>)로 이루어져있고, 행을 표시할 땐 \<tr\>를 쓴다.

### 예제 1 - 기본형

```html
<!doctype html>
<head>
    <meta charset="UTF-8">
    <style>
        table {
            width: 700px;
            border-collapse: collapse;
        }
        thead {
            color: red;
            font-size: 20px;
            text-align: center;
        }
        tbody {
            color: blue;
            text-align: left;
        }
        th, td {
            border: 1px solid gray;
            padding: 20px;
        }
        tr:nth-child(even) {
            background-color: gray;
        }

    </style>
</head>
<body>
<table>
    <caption>caption</caption>
    <thead>
    <tr>
        <th>번호</th>
        <th>이름</th>
        <th>나이</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>01</td>
        <td>홍길동</td>
        <td>20</td>
    </tr>
    <tr>
        <td>02</td>
        <td>서길동</td>
        <td>20</td>
    </tr>
    <tr>
        <td>03</td>
        <td>최길동</td>
        <td>20</td>
    </tr>
    </tbody>
</table>
</body>
</html>
```

![예제1](/assets/img/posts/html-004/result01.jpg)

### 예제 2 - 셀 병합

- colspan: 두 개 이상의 열을 하나로 합칠 때
- rowspan: 두 개 이상의 행을 하나로 합칠 때

```html
<!doctype html>
<head>
    <meta charset="UTF-8">
    <style>
        table {
            border-collapse: collapse;
        }
        td {
            border: 1px solid black;
            padding: 20px;
        }
    </style>
</head>
<body>
<table>
    <caption>caption</caption>
    <tr>
        <td rowspan="3" colspan="2">사진</td>
        <td rowspan="2">성명</td>
        <td rowspan="2" colspan="3">홍길동</td>
        <td rowspan="1" colspan="3">주민등록번호</td>
    </tr>
    <tr>
        <td colspan="4">123456-1234567</td>
    </tr>
    <tr>
        <td colspan="8">생년월일 12년 34월 56일</td>
    </tr>
    <tr>
        <td colspan="2">주소</td>
        <td colspan="8">서울시 ~~</td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2">연락처</td>
        <td >집</td>
        <td colspan="3">02-1234-5678</td>
        <td rowspan="2" colspan="2">이메일</td>
        <td rowspan="2" colspan="2">1234@1234.com</td>
    </tr>
    <tr>
        <td >핸드폰</td>
        <td colspan="3">010-1234-1234</td>
    </tr>
</table>
</body>
</html>
```
![예제2](/assets/img/posts/html-004/result02.jpg)