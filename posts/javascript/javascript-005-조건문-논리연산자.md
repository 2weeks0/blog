# [JavaScript] 조건문과 논리 연산자

## `if`문

- `condition`이 `true`면 `body`를 실행한다.

```javascript
if (condition) {
  // body
}
```

- 여러 조건을 붙일 땐, `else if`를 사용한다.

```javascript
if (condition1) {
  // body1
} else if (condition2) {
  // body2
} else {
}
```

### 조건부 연산자 `?`

- `자바`에서 `삼항연산자`와 같다.
- `condition`이 `true`면 `?`이하를, `false`면 `:`이하를 반환한다.

```javascript
let value = condition ? value1 : value2
let allow = (18 < age) ? true : false
```

## 논리 연산자

- 다른 언어와 똑같다.

|기능|연산자|
|:--:|:--:|
|OR|`\|\|`|
|AND|`AND`|
|NOT|`!`|

### `||` (OR)

- 피연산자 중 하나라도 `true`이면 결과가 `true`다.

```javascript
console.log(true || true) // true
console.log(true || false) // true
console.log(false || true) // true
console.log(false || false) // false
```

- `||` 연산자의 연산 순서는 아래와 같다.
  1. 가장 왼쪽 피연산자부터 시작해 오른쪽으로 나아간다.
  2. 각 피연산자를 `불린형`으로 변환하여 평가한다.
  3. 만약, 결과가 `true`라면 현재 피연산자의 값을 반환한다.
  4. 만약, 결과가 `false`라면 가장 마지막 피연산자의 값을 반환한다. (결과가 `false`라면 현재 피연산자가 곧 마지막 피연산자다.)

```javascript
console.log(false || 0) // 0
console.log(100 || false) // 100
let nickName = ""
let name = "홍길동"
console.log(nickName || name) // 홍길동
```

- 만약, 왼쪽 피연산자가 true면 오른쪽 피연산자는 실행되지 않는다.

```javascript
true || console.log("실행 X")
false || console.log("실행 O")
```

### `&&` (AND)

- 피연산자 중 하나라도 `false`면 결과가 `false`다.

```javascript
console.log(true && true) // true
console.log(true && false) // false
console.log(false && true) // false
console.log(false && false) // false
```

- `&&` 연산자의 연산 순서는 아래와 같다.
  1. 가장 왼쪽 피연산자부터 시작해 오른쪽으로 나아간다.
  2. 각 피연산자를 `불린형`으로 변환하여 평가한다.
  3. 만약, 결과가 `false`라면 현재 피연산자의 값을 반환한다.
  4. 만약, 결과가 `true`라면 가장 마지막 피연산자의 값을 반환한다. (결과가 `true`라면 현재 피연산자가 곧 마지막 피연산자다.)

```javascript
console.log(1 && -100) // -100
console.log(1 && 0) // 0
console.log(null && true) // null
```

- 만약, 왼쪽 피연산자가 false면 오른쪽 피연산자는 실행되지 않는다.

```javascript
true && console.log("실행 O")
false && console.log("실행 X")
```

### `!` (NOT)

- 단항 연산자로 피연산자를 `불린형`으로 변환한 후, 그 역을 반환한다.

```javascript
console.log(!0) // true
console.log(!100) // false
```

- `!!` 연산자를 사용하면 `불린형`으로 변환할 수 있다.

```javascript
console.log(!!0) // false
console.log(!!100) // true
```
