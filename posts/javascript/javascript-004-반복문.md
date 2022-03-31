# [JavaScript] 반복문

## `while` 반복문
- 자바와 똑같다.
- `condition`에는 `조건문`이 와야하며 true일 경우 `body` 부분이 반복된다.

```JavaScript
while (condition) {
    // body
}
```

## `do while` 반복문
- 자바와 똑같다.
- `do while` 문은 `body`를 1회 수행한 후, condition에 따라 반복 여부가 결정된다.

```JavaScript
do {
  // body
} while (condition)
```

## `for` 반복문
- 자바와 똑같다.

```JavaScript
for (begin; condition; step) {
  // body
}
```
|구성요소|예|설명|
|:--|:--:|:--|
|begin|`i=0`|반복문이 시작될 때, 한 번 실행된다.|
|condition|`i < 3`|반복마다 해당 조건을 확인한다. `true`면 반복된다.|
|step|`i++`|body가 실행된 후에 실행된다.|
|body|`console.log(i)`|본문|

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i)
}
console.log(i) // ReferenceError: i is not defined
```
- 위 예제에서는 `for`문 밖에서 `i`를 참조하고 있는데, `i`는 `인라인 변수`이기 때문에 `ReferenceError`가 발생한다.

## `break`, `continue`
- 자바와 똑같다.
- `break`: 반복문을 종료시킨다.
- `continue`: 현재 실행 중인 이터레이션을 멈추고, `step` 문을 실행한다.

```JavaScript
let i = 0
while (true) {
  if (i == 5) {
    break
  }
  console.log(i++) // 0, 1, 2, 3, 4 출력
}
```

```JavaScript
for (let i = 0; i < 10; i++) {
  if (i % 2 == 0) {
    continue
  }
  console.log(i) // 1, 3, 5, 7, 9 출력
}
```
