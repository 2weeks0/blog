# [네트워크] URI와 URL

## URI란? (Uniform Resource Indentifier)

특정 리소스를 식별하는 통합 자원 식별자를 의미한다. 인터넷 상에서 특정 자원을 나타내는 유일한 주소다.

```
scheme://host[:port][/path][?query]

scheme: 사용할 프로토콜. 웹에서는 http나 https 사용
host: IP주소
port: 포트 번호.
path: 서버 내 리소스 경로
query: 접근할 대상에게 전달하는 파라미터

ex)
http://IP주소:포트/폴더이름/파일이름
https://comic.naver.com/webtoon/list?titleId=798173&weekday=thu
```

## URL이란? (Uniform Resource Locator)

흔히 웹 주소라고도 하며, 컴퓨터 네트워크 상에서 리소스가 어디 있느지 알려주기 위한 규약이다. URL의 부분 집합이다.

## 차이점

URL은 주소나 특정 위치를 가르킨다. 마치 집 주소와 같다. 또, URL은 URI이기도 하다. 주소로 식별이 가능하기 때문이다. URI의 예는 이름이 있다. 이름은 URI이지만 URL은 아니다. 아까 언급한 URI가 URL보다 큰 범주에 있기 때문에 이름은 URI이면서 URL이 아닌 예가 된다.