# [JavaScript] var

ES6 이전 버전에서는 `var`로 변수를 선언하여 사용했다.
현재는 `let`과 `const`에 의해 완전히 대체되었지만, ES6 이전 버전에 작성된 스크립트에서는 `var`를 사용했기 때문에 `var`란 녀석이 어떤 녀석인지 알아야할 필요가 있다.
물론, 알아두기만 하고 사용해서는 안된다!!

기본적으로 `var`와 `let`은 매우 유사하다.
`var`로 작성된 스크립트에를 `let`으로 바꾸어도 문제 없이 동작할 경우는 높다.
하지만 무시할 수 없는 차이점이 있는데, 이 때문에 많은 개발자가 고통받았고, `let`과 `const`가 탄생하게 되었다.
그럼 `var`의 특징을 알아보자.

## 블록 스코프가 없다.

`var`로 선언한 변수는 함수 스코프이거나 전역 스코프다.

```javascript
{
    var num = 1;
}
console.log(num); // 1
```

반면에 `let`으로 선언하면 에러가 발생한다.

```javascript
{
    let num = 1;
}
console.log(num); // ReferenceError: num is not defined
```

함수 내에서 `var`를 사용해 변수를 선언했다면 해당 함수 내에서만 사용할 수 있다.

```javascript
function f() {
    var num = 1;
    console.log(num); // 1
}

f();
console.log(num); // ReferenceError: num is not defined
```

## 중복 선언이 가능하다.

일반적으로 프로그래밍 언어에서 동일한 이름의 변수를 여러 번 선언하면 에러가 발생한다.
하지만 이 특별한 `var` 녀석은 중복 선언을 허용한다.

```javascript
var num = 1;
var num = 2;
console.log(num); // 2
```

역시 `let`으로 중복 선언을 하면 에러가 발생한다.

```javascript
let num = 1;
let num = 2; // SyntaxError: Identifier 'num' has already been declared
console.log(num);
```

## 선언하기 전에 사용 가능하다.

블록 스코프가 없다는 것은 어떻게 보면 이해할 수도 있는 부분이었다.
중복 선언이 가능하다는 것은 이해가 되지 않지만 이해하려 노력할 수 있는 부분이다.
(사실 이해하려 노력할 수 없을 것 같다.)
하지만 선언하기 전에 사용할 수 있다는 것은 정말 골 때리는 특징인 것 같다.
예제를 통해 살펴보자.

```javascript
num = 1;
console.log(num);
var num;
```

`var`로 선언한 num 변수를 선언하기도 전에 값을 할당할 수 있고, 참조할 수 있다.
이렇게 변수의 선언문이 먼저 수행되는 것을 호이스팅(hoisting)이라고 한다.

### 호이스팅

`var`로 선언한 모든 변수는 함수의 최상단으로 끌어 올려진다.
앞선 예제 코드는 사실 아래와 같이 동작한다.

```javascript
var num; // 호이스팅 (위로 끌어올려짐)
num = 1;
console.log(num);
// var num;
```

하지만 할당은 호이스팅되지 않고, 선언부만 호이스팅된다.

```javascript
console.log(num); // undefined
var num = 1;
```

