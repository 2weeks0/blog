# [JavaScript] switch

- 여러 `if` 문을 `switch`으로 나타낼 수 있다.
- `if`와 기능은 같지만 가독성이 좋아진다.

```javascript
switch (a) {
  case value1:
    // body1
    break
  case value2:
    // body2
    break
  default:
    // body3
    break
}
```

- 변수 `a`의 값이 `value1`과 일치한다면 `body1` 구문을 실행한다.
- 만약, 변수 `a`의 값이 `value1`과 일치하지 않고, `value2`와 일치하다면 `body2` 구문을 실행한다.
- 만약, 변수 `a`의 값이 `value1`과 일치하지 않고, `value2`와도 일치하지 않다면 `body3` 구문을 실행한다.

```javascript
let a = "3"

switch (a) {
  case "1":
    console.log("실행 X")
    break;
  case "2":
    console.log("실행 X")
    break;
  case 3:
    console.log("실행 X")
    break;
  default:
    console.log("실행 O")
    break;
}
```
