# [JavaScript] 나머지 매개변수와 스프레드 문법

자바스크립트의 함수는 인수의 개수의 제약이 없다.

```javascript
function sum(a, b) {
    return a + b;
}

console.log(sum(1)); // NaN
console.log(sum(1, 1)); // 2
console.log(sum(1, 1, 1, 1, 1)); // 2
```

함수를 정의할 땐, 인자가 2개로 정했지만 호출할 땐 2개가 아닌 개수를 넣어도 에러가 발생하지 않는다.
다만, 결과는 앞의 인자 2개만 활용한다.

인자의 개수를 정하지 않을 땐, `...`(나머지 매개변수)을 붙여주면 된다.

```javascript
function sum(...nums) {
    let result = 0;
    for (let num of nums) {
        result += num;
    }
    return result;
}

console.log(sum(1)); // 1
console.log(sum(1, 1)); // 2
console.log(sum(1, 1, 1, 1, 1)); // 5
```

## arguments 객체

유사 배열 객체인 `arguments`를 이용해 인자에 접근할 수 있다.
나머지 매개변수 `...`은 최신 문법이기 때문에, 예전 코드에선 `arguments`를 이용해야했다.

```javascript
function sum() {
    let result = 0;
    for (let num of arguments) {
        result += num;
    }
    return result;
}

console.log(sum(1)); // 1
console.log(sum(1, 1)); // 2
console.log(sum(1, 1, 1, 1, 1)); // 5
```

다만, `arguments`는 모든 인자를 다 담기 때문에 나머지 매개변수 `...`과 차이가 있다.

```javascript
function sum1(first, second, ...rest) {
    let result = first + second;
    for (let num of rest) {
        result += num;
    }
    return result;
}

console.log(sum1(1, 1, 1, 1, 1)); // 5

function sum2(first, second) {
    let result = first + second;
    for (let num of arguments) {
        result += num;
    }
    return result;
}

console.log(sum2(1, 1, 1, 1, 1)); // 7

function sum3(first, second) {
    let result = first + second;
    let [f, s, ...rest] = arguments;
    for (let num of rest) {
        result += num;
    }
    return result;
}

console.log(sum3(1, 1, 1, 1, 1)); // 5
```

## 스프레드 문법

위에서 만든 나머지 매개변수를 이용한 함수에 배열을 매개변수로 넘겨줘야할 때, 아래와 같이 쓸 수 있다.

```javascript
function sum(...nums) {
    let result = 0;
    for (let num of nums) {
        result += num;
    }
    return result;
}

let arr1 = [1, 1, 1];
console.log(sum(...arr1)); // 3

let arr2 = [1, 1, 1];
console.log(sum(...arr1, ...arr2)); // 6
```