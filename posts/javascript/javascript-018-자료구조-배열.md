# [JavaScript] 자료구조-배열

## 배열

2가지 방법으로 배열을 생성할 수 있다.

```javascript
let arr1 = new Array();
let arr2 = [];
```

`[]` 로 해당 index의 요소에 접근할 수 있다.

```javascript
let arr = ["a", "b"];

console.log(arr[0]); // a
console.log(arr[2]); // undefined

arr[2] = "c";
console.log(arr[2]); // c
```

`length` 프로퍼티로 배열의 길이를 알 수 있다.

```javascript
let arr = [1, 2, 3];

console.log(arr.length); // 3
```

## `push`/`pop`과 `shift`/`unshift`

배열을 큐(queue)처럼 사용할 수 있다.
- `push`: 맨 끝에 요소를 추가한다.
- `shift`: 맨 앞에 요소를 반환하고 제거한 뒤, 앞으로 한 칸씩 땡긴다. (시간복잡도가 O(N)이다.)

```javascript
let queue = [];
queue.push(3);
queue.push(2);
queue.push(1);

console.log(queue.shift()); // 3
console.log(queue.shift()); // 2
console.log(queue.shift()); // 1
```

배열을 스택(stack)처럼 사용할 수 있다.
- `push`: 맨 끝에 요소를 추가한다.
- `pop`: 맨 끝 요소를 반환하고 제거한다.

```javascript
let stack = [];
stack.push(3);
stack.push(2);
stack.push(1);

console.log(stack.pop()); // 1
console.log(stack.pop()); // 2
console.log(stack.pop()); // 3
```

`unshift`: 맨 앞에 요소를 추가하고, 한 칸씩 뒤로 민다. (역시 O(N))

## 반복문

`for`문으로 배열을 순회할 수 있다.

```javascript
let arr = [1, 2, 3];

for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
for (let it of arr) {
    console.log(it);
}
```

## `length` 프로퍼티

배열에 요소를 추가하거나 삭제하면 `length`가 자동 갱신된다. 사실 `length`는 마지막 index에 1을 더한 값으로 저장된다.

```javascript
let arr = [];
arr[5] = 1;
console.log(arr.length); // 6
```

`length`에 값을 할당할 수도 있다.

```javascript
let arr = [1, 2, 3];
arr.length = 1;
console.log(arr); // [1]

arr.length = 0;
console.log(arr) // []
```