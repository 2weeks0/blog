# [JavaScript] 자료구조-문자열

## 문자열의 길이

`length` 프로퍼티로 문자열의 길이를 알 수 있다. (함수가 아니다!!)

```javascript
console.log("asd".length); // 3, length()가 아님!!
```

## `charAt`과 `[]`

문자열의 특정 index의 문자열을 반환할 때, 사용한다.

```javascript
const str = "Hello";

console.log(str.charAt(0)); // H
console.log(str[0]); // H

console.log(str.charAt(10)); // "" (빈 문자열)
console.log(str[10]); // undefined
```

`charAt`보다 `[]`을 권장한다.
차이점은 해당 index에 해당하는 문자열을 반환할 수 없을 때 나타난다.
- `charAt`: 빈 문자열 반환
- `[]`: `undefined` 반환

## 불변성

문자열은 불변하다. (java와 같다)

## 대소문자 변경

`toUpperCase()`와 `toLowerCase()`를 사용하여 대/소문자로 변경할 수 있다.

```javascript
const str = "Hello";

console.log(str.toUpperCase()); // HELLO
console.log(str.toLowerCase()); // hello
```

## 부분 문자열 찾기

`indexOf(subStr, pos)` 메소드는 `pos`에서부터 시작해 `subStr`의 index를 반환해주는 메소드다.

```javascript
const str = "Hello Hello";

console.log(str.indexOf("Hello")); // 0
console.log(str.indexOf("asd")); // -1, 못 찾을 땐 -1 반환
console.log(str.indexOf("Hello", 1)); // 6, index가 1인 곳부터 찾으므로
```

`lastIndexOf(subStr, pos)` 메소드는 반대로 생각하면 된다.
문자열 끝에서부터 찾고, 마지막 index를 반환한다.

```javascript
const str = "Hello Hello";

console.log(str.lastIndexOf("Hello")); // 0
console.log(str.lastIndexOf("asd")); // -1, 못 찾을 땐 -1 반환
console.log(str.lastIndexOf("Hello", 1)); // 6, index가 1인 곳부터 찾으므로
```

`includes(subStr, pos)`는 `indexOf` 메소드와 유사하며 결과가 `Boolean`형으로 반환된다.

```javascript
const str = "Hello Hello";

console.log(str.includes("Hello")); // true
console.log(str.includes("asd")); // false
console.log(str.includes("Hello", 1)); // true
```

`startsWith(subStr)` 와 `endsWith(subStr)`은 해당 문자열이 subStr으로 시작/끝인지를 판별한다.

```javascript
const str = "Hello Hello";

console.log(str.startsWith("Hello")); // true
console.log(str.startsWith("asd")); // false
console.log(str.endsWith("Hello")); // true
```

## 부분 문자열 추출하기

자바스크립트엔 부분 문자열 추출 메소드가 세 가지 있다.

`slice(start, end)`: start부터 end전 까지 반환

```javascript
const str = "Hello";

console.log(str.slice(0, 1)); // H
console.log(str.slice(1)); // ello
console.log(str.slice(-5)); // Hello, -를 붙이면 뒤에서 센다
```

`substring(start, end)`: start와 end 사이에 있는 문자열 반환한다.
`slice`와 유사하지만 start가 end보다 커도 되고, 음수를 넣으면 0으로 인식된다.

```javascript
const str = "Hello";

console.log(str.substring(0, 1)); // H
console.log(str.substring(1, 0)); // H
console.log(str.substring(-5)); // Hello, 음수를 넣으면 0으로 인식된다.
```

`substr(start, length)`: start에서 시작해 length 길이의 문자열을 반환한다.

```javascript
const str = "Hello";

console.log(str.substr(0, 1)); // H
console.log(str.substr(1)); // ello
console.log(str.substr(-5, 2)); // He
```

## 문자열 비교하기

`localeCompare(str)`을 사용하면 문자 코드를 통한 비교가 아닌 사전순 비교가 가능하다.

```javascript
console.log("a" > "A"); // true, a의 code값이 A보다 크기 때문
console.log("a".codePointAt(0)); // 97
console.log("A".codePointAt(0)); // 65

console.log("a".localeCompare("A")) // -1
```