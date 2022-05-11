# [JavaScript] 생성자 함수

- 생성자 함수는 일반 함수와 차이점이 없지만, 두 관례를 따른다.
    1. 함수 이름의 첫 글자는 대문자
    2. `new` 키워드를 붙여 실행
    
```javascript
function Data(name) {
    this.name = name;
}

let data = new Data("안녕");

console.log(data.name);
```

new Data(...) 함수는 다음과 같이 동작한다.

1. 빈 객체를 만들어 `this`에 할당한다.
2. 함수 본문을 실행한다. `this`에 name 프로퍼티를 추가한다.
3. `this`를 반환한다.

즉, 아래처럼 동작한다.

```javascript
function Data(name) {
    // this = {}; (새로운 객체 생성)
    this.name = name;
    // return this; (생성한 객체 반환)
}
```