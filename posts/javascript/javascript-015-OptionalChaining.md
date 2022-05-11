# [JavaScript] Optional Chaining `?.`

## `?.`

- Optional Chaining `?.`을 사용하면 값이 없는 중첩 객체를 안전하게 접근할 수 있다.
- `kotlin`, `dart`에서의 `null-safety`와 같은 맥락같다.
- 어떤 상황에서 사용하는지 알아보자.

```javascript
let student = {};

console.log(student.score.math); // TypeError: Cannot read properties of undefined (reading 'math')  
```

- 위와 같이 어떠한 객체 안에 존재하지 않은 프로퍼티를 참조하면 에러가 발생한다.
- 이 때, 에러 없이 안전하게 접근하기 위해 `null` 이거나 `undefined`일수도 있는 객체 뒤에 `?.`를 붙여준다.

```javascript
let student = {};

console.log(student.score?.math); // undefined  
```

- 즉, `student` 객체에 `score` 프로퍼티가 있다면 `score` 프로퍼티의 `math` 프로퍼티를 참조하겠다는 뜻이다.

## 단락 평가 (short-circuit)

- `?.`는 `||`, `&&` 연산자와 마찬가지로 왼쪽 값이 없으면 즉시 평가를 멈춘다.
- 즉, `?.` 왼쪽 값이 `null` 또는 `undefined`라면 오른쪽에 있는 평가는 진행되지 않는다.

```javascript
let sayHello = () => console.log("Hello~");
let data = {
    sayHello
};

data?.sayHello(); // Hello~

data = null;
data?.sayHello(); // 아무 동작이 없다.
```

## `?.()`와 `?.[]`

- `?.`은 연산자가 아니다.
- 따라서, `?.` 뒤에 `()`를 붙여 함수를 실행시키거나, `[]`를 붙여 프로퍼티에 접근할 수 있다.

```javascript
let sayHello = () => console.log("Hello~");
let data = {
    name: "이름",
    sayHello
};

console.log(data?.["name"]); // 이름
data.sayHello?.(); // Hello~

delete data.sayHello;
data.sayHello?.(); // 아무 동작이 없다.
```

