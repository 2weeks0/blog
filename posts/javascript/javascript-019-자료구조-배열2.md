# [JavaScript] 자료구조-배열2

배열 객체의 메소드 사용법을 알아보자.

## 요소 추가/제거

### `splice`

요소를 자유자재로 추가, 삭제, 교체할 수 있다.
```javascript
splice(start: number, deleteCount?: number): T[];
splice(start: number, deleteCount: number, ...items: T[]): T[];
```

start로부터 deleteCount 개수를 삭제할 수 있고, items를 인자로 주면 교체해준다.

```javascript
const arr = [1, 2, 3];

arr.splice(0, 1);
console.log(arr); // [2, 3]

arr.splice(0, 0, 0, 1);
console.log(arr); // [0, 1, 2, 3]
```

### `slice`

```javascript
slice(start?: number, end?: number): T[];
```

start 부터 end 이전까지의 배열을 복사해 새로운 배열을 반환한다.

```javascript
const arr1 = [1, 2, 3];
const arr2 = arr1.slice();

console.log(arr1); // [1, 2, 3]
console.log(arr2); // [1, 2, 3]
console.log(arr1 === arr2); // false
```

### `concat`

```javascript
concat(...items: ConcatArray<T>[]): T[];
concat(...items: (T | ConcatArray<T>)[]): T[];
```

기존 배열 요소를 사용해 새로운 배열을 만든다.

```javascript
const arr = [1, 2, 3];

console.log(arr.concat(4, 5)); // [1, 2, 3, 4, 5]
console.log(arr.concat([4, 5])); // [1, 2, 3, 4, 5]
console.log(arr.concat([4, 5], 6)); // [1, 2, 3, 4, 5, 6]
```

## `forEach`

`forEach`로 반복 작업을 수행할 수 있다.

```javascript
const arr = ["a", "b", "c"];

arr.forEach((item, index, array) => {
    console.log(item, index, array);
});
// a 0 [ 'a', 'b', 'c' ]
// b 1 [ 'a', 'b', 'c' ]
// c 2 [ 'a', 'b', 'c' ]
```

## 배열 탐색하기

### `indexOf`, `lastIndexOf`, `includes`

이전에 문자열 메소드에서 다뤘던 친구들과 같은 역할을 한다.

- `indexOf(item, from)`은 from 부터 시작해 item 요소를 찾는다. 발견하면 index를, 못하면 -1을 반환한다.
- `lastIndexOf(item, from)`은 뒤에서부터 찾는 `indesOf`다.
- `includes(item, from)`은 from부터 시작해 item 요소가 있으면 true, 없으면 false를 반환한다.

```javascript
const arr = [1, 2, 3];

console.log(arr.indexOf(1)); // 0
console.log(arr.indexOf(4)); // -1
console.log(arr.includes(1)); // true
console.log(arr.includes(4)); // false
```

### `find`와 `findIndex`

함수를 인자로 받아 조건에 맞는 요소가 있으면 요소/index를 반환한다.

```javascript
const arr = [
        {name: "LEE"},
        {name: "PARK"},
        {name: "KIM"},
    ];

console.log(arr.find(it => it.name === "LEE")); // { name: 'LEE' }
console.log(arr.find(it => it.name === "CHOI")); // undefined

console.log(arr.findIndex(it => it.name === "LEE")); // 0
console.log(arr.findIndex(it => it.name === "CHOI")); // -1
```

### `filter`

말 그대로 필터링을 해준다. 조건에 맞는 요소들을 담은 새로운 배열을 반환한다.

```javascript
const arr = [
        {name: "LEE", country: "KOREA"},
        {name: "TOM", country: "USA"},
        {name: "KIM", country: "KOREA"},
    ];

console.log(arr.filter(it => it.country === "KOREA")); // [ { name 'LEE', country: 'KOREA' },  { name: 'KIM', country: 'KOREA' } ]
```

## 배열을 변형시키는 메소드

### `map`

배열을 순회하면서 각 요소를 새로운 값으로 변환하여 새로운 배열을 반환한다.

```javascript
const arr = [
        {name: "LEE", country: "KOREA"},
        {name: "TOM", country: "USA"},
        {name: "KIM", country: "KOREA"},
    ];

console.log(arr.map(it => it.name)); // [ 'LEE', 'TOM', 'KIM' ]
```

### `sort`

말 그대로 정렬해주는 메소드다. 인자로 정렬 조건을 넘겨줄 수 있다.

```javascript
const arr = [1, 2, 10];

arr.sort();

console.log(arr); // [ 1, 10, 2 ]
```

주의사항!!
위 결과를 보면 알 수 있듯이, 정렬할 때, 문자열로 변환 후 정렬하기 때문에 사전 순 정렬이 된다. 오름차순으로 정렬하기 위해선 정렬 조건을 인자로 넣어줘야 한다.

```javascript
const arr = [1, 2, 10];

arr.sort((a, b) => a - b);

console.log(arr); // [ 1, 2, 10 ]
```

### `reverse`

역순으로 정렬시켜준다.

```javascript
const arr = [1, 2, 3];

arr.reverse();

console.log(arr); // [ 3, 2, 1 ]
```

### `split`과 `join`

- `str.split(str2)`: 문자열을 str을 기준으로 자르고, 결과를 배열로 반환한다.
- `arr.join(str)`: 배열의 요소들에 str을 더한 후, 결과를 문자열로 반환한다.

```javascript
const str = "KIM,LEE,PARK";
const arr = str.split(",");
const str2 = arr.join("!");

console.log(arr); // [ 'KIM', 'LEE', 'PARK' ]
console.log(str2); // KIM!LEE!PARK
```

### `reduce`와 `reduceRight`

`reduce`는 순회하며 특정 연산을 시행하고, 그 연산 값을 다음 반복 때 사용할 수 있는 메소드다.

```javascript
reduce(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T): T;
reduce(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T, initialValue: T): T;
```

예를 들어보자.

```javascript
const arr = [1, 2, 3];

const sum = arr.reduce((sum, it) => {
        console.log(sum, it);
        return sum + it;
    }, 0);
// 0 1
// 1 2
// 3 3
console.log(sum); // 6
```

initialValue 로 0을 주었으므로 처음 반복 땐, sum에 0이 출력된 것을 볼 수 있다.
initialValue는 생략할 수도 있는데, 생략할 경우 처음 반복 때의 previousValue에 첫번째 인자를 사용하고, 두번째 값부터 반복이 시작된다. 따라서, 길이가 0인 배열로 해당 작업을 진행할 경우, 에러가 뜬다.

```javascript
const arr = [1, 2, 3];

const sum = arr.reduce((sum, it) => {
        console.log(sum, it);
        return sum + it;
    });
// 1 2
// 3 3
console.log(sum); // 6

const arr2 = [];
const sum2 = arr2.reduce((sum, it) => sum + it); // TypeError: Reduce of empty array with no initial value
```

## `Array.isArray`

배열은 object 타입(객체)이다. 따라서, 배열인지 아닌지 판별할 때는 `Array.isArray` 메소드를 사용한다.

```javascript
const arr = [];

console.log(Array.isArray(arr)); // true
```