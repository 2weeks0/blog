# [JavaScript] 자료형과 형 변환

# 자료형
- 5가지 기본 자료형(primitive type)이 있다.

|자료형|typeof 출력값|설명|
|:---:|:---:|---|
|숫자형|number|정수 또는 실수형|
|문자열형|string|문자열|
|불린형|boolean|true or false|
|undefined|undefined|변수가 선언되었지만 초기화가 되지 않는 경우|
|null|object|값이 존재하지 않을 경우|

## 숫자형 (Number)
- 숫자형은 정수 및 부동소수점 숫자를 나타낸다.
```javascript
let n = 123
n = 12.3
```

- 일반적인 숫자 외에 Infinity(양의 무한), -Infinity(음의 무한), NaN(Not a Number)과 같은 특수 문자가 있다.
```javascript
let n = 1 / 0 // Infinity
n = -1 / 0 // -Infinity
n = "문자열" / 1 // NaN
```

## BigInt
- 숫자형엔 -(2^53 - 1) ~ (2^53 - 1)의  범위를 갖는다.
- 따라서, BigInt 형의 자료형으로 매우 큰/작은 숫자를 표현할 수 있다.
- BigInt 형을 사용하기 위해선 정수 끝에 n을 붙이면 된다.

```javascript
const bigInt = 1234567890123456789012345678901234567890n;
console.log(typeof bigInt) // bigint
```


## 문자형 (String)
- C, Java와 다르게 Character 자료형이 없다. (문자가 하나 이상 들어갈 수 있다.)
- 문자열을 나타날 땐, 3가지 방법이 있다.
1. 큰 따옴표: "hello"
2. 작은 따옴표: 'hello'
3. 백틱: `hello`, 백틱 내에 변수나 표현식을 ${}로 감싸면 쉽게 데이터를 끼워넣을 수 있다.

```javascript
let str = "hello"
let str2 = 'hello'
let str3 = `hello ${str}` // hello hello
let str4 = `1 + 2 = ${1 + 2}` // 1 + 2 = 3
```

## 불린형 (Boolean)
- 논리 타입으로 true, false 두 값이 존재한다.
```javascript
let b = 1 == 1 // true
let b1 = false
```

## undefined
- 할당되지 않은 상태를 나타내는 자료형이다.
- 변수를 선언했지만 할당하지 않는다면 undefined가 할당된다.
```javascript
let temp
console.log(temp) // undefined
```

## null
- null 값은 오직 null 값을 위한 자료형이다.
- java에서는 null pointer를 뜻하지만 자바스크립트에선 존재하지 않는, 알 수 없는 값을 나타나는 데 사용한다.
```javascript
let temp = null
console.log(temp) // null
```

# 형 변환
- 함수와 연산자에 전달되는 값은 적절한 자료형으로 자동 변환된다.

### 숫자형으로 변환
```javascript
console.log("6" * "3") // 18
console.log(Number("123")) // 123
console.log(Number("넘버")) // NaN (Not a Number, 형 변환 실패)
console.log(Number(true)) // 1
console.log(Number(false)) // 0
console.log(Number(null)) // 0
console.log(Number(undefined)) // NaN
```

### 불린형으로 변환
```javascript
console.log(Boolean("")) // false (빈 문자열이기 때문)
console.log(Boolean("adfasdf")) // (비어있지 않기 때문)
console.log(Boolean("0")) // true
console.log(Boolean(" ")) // true
console.log(Boolean(null)) // false
console.log(Boolean(undefined)) // false
```
