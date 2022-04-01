# [JavaScript] 조건문

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
  // body3
}
```

## 조건부 연산자 `?`

- `자바`에서 `삼항연산자`와 같다.

```javascript
let value = condition ? value1 : value2
let allow = (18 < age) ? true : false
```
