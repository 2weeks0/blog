### [JavaScript] 변수와 상수

- ECMAScript 6 부터 let, const 키워드가 생김
- ECMAScript 5 이전엔 var 키워드로 변수를 생성함

|키워드|구분|선언 위치|재선언|
|:---:|:---:|:---:|:---:|
|var|변수|전역 스코프|가능|
|let|변수|해당 스코프|불가능|
|const|상수|해당 스코프|불가능|

- var와 const는 같은 스코프에서 사용할 수 있다. (지역 변수 느낌?)
```JavaScript
{
    var v = 1
    let l = 1
    const c = 1
}
{
    console.log(v) // 1
    console.log(l) // 에러 남!! ReferenceError: c is not defined
    console.log(c) // 에러 남!! ReferenceError: c is not defined
}
```

- var는 같은 이름의 변수를 재선언할 수 있다.
```JavaScript
{
    var num = 1
    console.log(num) // 1
    var num = 2
    console.log(num) // 2  
}
{
    let num2 = 1
    console.log(num2) // 1
    let num2 = 2 // 에러 남!! SyntaxError: Identifier 'num2' has already been declared
    console.log(num2)   
}
```

## 요약
var, let, const 키워드로 변수를 선언할 수 있다.
- let -> 일반적으로 사용하는 변수 선언 키워드.
- var -> 잘 사용하지 않는 변수 선언 키워드. 지역 변수 쓸 때 사용.
- const -> let과 비슷하나 값 변경 불가능.
