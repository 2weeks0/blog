# [JavaScript] 함수

- 프로그래밍을 하다보면 유사한 동작을 하는 코드를 여러 곳에 작성해야하는 경우가 있다. 이럴 때마다, 동일한 코드를 여러 군데 작성하는 것은 매우 비효율적이다. 이를 해결할 수 있는 함수에 대해 알아보자.

## 함수 선언

- 함수 선언이란 함수를 만드는 행위를 말한다. 함수는 아래와 같이 만들 수 있다.

```javascript
function print(msg) {
    console.log(msg)
}

print("안녕하세요") // 안녕하세요
```

- `function` 키워드, 함수 이름, 매개 변수를 괄호로 둘러싸주면 함수를 선언할 수 있다.
- `print("안녕하세요")`로 함수를 호출하면 선언한 함수 본문이 실행된다.

## 지역 변수 (local variable)

- 함수 내에서 선언한 변수를 지역 변수(local variable)이라고 하며, 이는 함수 안에서만 접근할 수 있다.

```javascript
function print() {
    let msg = "안녕하세요"
    console.log(msg)
}

print()
console.log(msg) // ReferenceError: msg is not defined
```

## 매개변수 (parameter)

- 매개변수를 통해서 함수에 데이터를 전달할 수 있다.
```javascript
function print(msg) {
    console.log(msg)
}
```

### 기본값

- 매개변수에 데이터를 전달하지 않으면 `undefined`가 전달된다.
- 따라서, 여러 개의 매개변수를 갖는 함수에 그 미만의 매개변수를 전달해줘도 에러가 발생하지 않는다.

```javascript
function print(msg1, msg2) {
    console.log(`msg1: ${msg1}, msg2: ${msg2}`)
}

print("안녕하세요") // msg1: 안녕하세요, msg2: undefined
print("안녕하세요", "여러분") // msg1: 안녕하세요, msg2: 여러분
print(1, 2) // msg1: 1, msg2: 2
```

- 이 때, 기본값을 `undefined` 가 아닌 다른 값으로 바꿔줄 수 있다.

```javascript
function print(msg = "msg") {
    console.log(`msg: ${msg}`)
}

print("안녕하세요") // msg: msg
```

또는

```javascript
function print(msg) {
    if (msg === undefined) {
        msg = "msg"
    }
    console.log(`msg: ${msg}`)
}

print() // msg: msg
```

### 반환 값 (return value)

- 함수를 호출했을 때, 특정 결과를 반환하게 만들 수 있다. 이를 반환 값이라고 한다.

```javascript
function sum(a, b) {
    return a + b
}

console.log(sum(1, 1)) // 2
```