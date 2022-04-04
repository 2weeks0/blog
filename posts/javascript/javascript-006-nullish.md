# [JavaScript] nullish 연산자 ??

- `a ?? b` 의 결과는 아래와 같다.
1. `a`가 `null`도 아니고  `undefined`도 아니면  `a`
2.  그 외 경우는 `b`

```javascript
x = a ?? b
x = (a != null && a != undefined) ? a : b
```

- 위 두 줄은 같은 동작을 하는 코드다.


### `??`와 `||`의 차이

- `||`는 첫 번째 true 값을 반환합니다.
- '??'는 첫 번째 정의된(defined) 값을 반환합니다.

```javascript
let a = 0

console.log(a || 1) // 1
console.log(a ?? 1) // 0
```
