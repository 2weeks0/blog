# [JavaScript] 화살표 함수

- 자바에서 람다라고 불리우는 함수 축약식이 자바스크립트에선 화살표 함수다.

```javascript
let sum = (a, b) => {
    return a + b;
} 
console.log(sum(1, 2)); // 3

let double = n => 2 * n;
console.log(double(2)); 

let sayHello = () => console.log("Hello~");
sayHello(); // Hello~
```

- 화살표 함수의 특징은 아래와 같다.
    1. 인자가 0개 일 땐, 괄호를 꼭 붙여줘야 한다.
    2. 인자가 1개일 땐, 괄호를 생략할 수 있다.
    3. 인자가 2개 이상일 땐, 괄호로 꼭 감싸주어야 한다.
    4. 함수 본문이 1줄일 땐, 중괄호 및 `return` 키워드를 생략할 수 있다.
    5. 함수 본문이 2줄 이상일 땐, 중괄호가 필수고, 반환값이 있다면 `return` 키워드를 꼭 붙여줘야 한다.