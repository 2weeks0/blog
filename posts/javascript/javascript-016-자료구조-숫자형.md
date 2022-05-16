# [JavaScript] 자료구조-숫자형

- 자바스크립트에서 숫자는 두 가지 자료형으로 나눌 수 있다.
    1. Number (64비트 부동소수점 숫자로 저장, -2^53 <= x <= 2^53)
    2. BigInt (길이에 제한 없음)
    
## Number

### 입력 방법

- 0의 개수가 많을 땐, `e`를 붙이고 0의 개수를 붙여주면 헷갈리지 않게 표현할 수 있다. 

```javascript
let billion1 = 1000000000;
let billion2 = 1e9;

console.log(billion1); // 1000000000
console.log(billion2); // 1000000000

let ms1 = 0.001;
let ms2 = 1e-3;

console.log(ms1); // 0.001
console.log(ms2); // 0.001
```

- 16진수는 `0x`, 8진수는 `0o`, 2진수는 `0b`를 붙여 표현할 수 있다.

```javascript
console.log(0xfF); // 255
console.log(0b11111111); // 255
console.log(0o377); // 255
```

### toString(base)

- `toString(base)` 메소드는 `base` 진법으로 변환 후, 문자열로 반환해준다.
- `base`의 default 값은 10이다.

```javascript
let num = 255;

console.log(num.toString(16)); // ff
console.log(Number(255).toString(8)); // 11111111
console.log((255).toString(2)); // 377
console.log(255..toString()); // 255
```

- 위 예제 코드를 보면 알 수 있듯이, `255` 에서 바로 함수를 호출하려면 `..` 점을 2개 붙이거나, 괄호로 감싸주면 된다.

### 어림 수 구하기

- `Math.floor`: 소수점 첫째 자리에서 버림
- `Math.ceil`: 소수점 첫째 자리에서 올림
- `Math.round`: 소수점 첫째 자리에서 반올림
- `Math.trunc`: 소수부를 무시하고, 정수부만 취함
- `toFixed(n)`: 소수 n+1자리에서 반올림하여 문자열로 반환

```javascript
let num = 1.234

console.log(Math.floor(num * 100) / 100); // 1.23 (숫자)
console.log(num.toFixed(2)); // 1.23 (문자열)
console.log(+num.toFixed(2)); // 1.23 (숫자)
```

- 위처럼 소수 첫째자리가 아닌, 다른 자리에서 연산을 취하고자 한다면 적당한 수를 곱한 뒤 나누면 된다.
- `toFixed` 메소드 후에 숫자형으로 반환하길 원한다면 앞에 `+`를 붙여주자.

### `isNaN`과 `isFinite`

`isNaN(n)`: n을 숫자로 변환한 다음 `NaN`인지 판별 (`NaN` === `NaN`이 `false`이기 때문에 해당 함수가 필요함)

```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN("asd")); // true
console.log(isNaN(123)); // false
console.log(isNaN("123")); // false
```

`isFinite(n)`: n을 숫자로 변환한 다음 숫자가 `Nan/Infinity/-Infinity` 이 아닌지 판별

```javascript
console.log(isFinite(NaN)); // false
console.log(isFinite(-Infinity)); // false
console.log(isFinite(Infinity)); // false
console.log(isFinite(1e100000)); // false
console.log(isFinite(1)); // true
```

### `parseInt` 와 `parseFloat`

- 위에서 `+` 연산자 또는 `Number()`를 사용하여 숫자형으로 변환했었다.
- 하지만, 위 방법은 숫자형으로 변환할 수 없을 경우에 `NaN`을 반환한다. 하지만 이번에 소개할 `parseX` 메소드를 사용하면 더 많은 곳에서 숫자형으로 반환할 수 있다.

```javascript
console.log(parseInt("100cm")); // 100
console.log(parseInt("100$")); // 100

console.log(parseInt("100.1cm")); // 100
console.log(parseFloat("100.1cm")); // 100.1
console.log(parseFloat("100.1.1.1.1cm")); // 100.1, 첫 번째 점까지 읽음

console.log(parseInt("a1")); // NaN, 첫 글자부터 숫자가 아니므로

console.log(parseInt("0xff", 16)); // 255
console.log(parseInt("ff", 16)); // 255
```

### 기타 수학 함수

- 자바스크립트 내장 객체인 `Math`에 여러 수학 메소드와 상수가 있다.

`Math.random()`: 0과 1 사이의 난수 반환
`Math.max(a, b, c, ...)`: 인수 중 최대값 반환
`Math.min(a, b, c, ...)`: 인수 중 최소값 반환
`Math.pow(n, power)`: n^power 반환

## BigInt

### 입력 방법

- 끝에 `n`을 붙이거나 `BigInt()`로 호출한다.

```javascript
console.log(10294159871298347189571289743891275n); // 10294159871298347189571289743891275n
console.log(BigInt("10294159871298347189571289743891275")); // 10294159871298347189571289743891275n
```

### 수학 연산자

```javascript
console.log(5n + 2n); // 7n
console.log(5n / 2n); // 2n, 결과가 BigInt 형이기 때문에 소수부는 버린다.
```

## 비교 연산자

```javascript
console.log(1n < 2n); // true
console.log(1 < 2n); // true
console.log( 1 == 1n ); // true
console.log( 1 === 1n ); // false, type이 다르기 때문
```

## 논리 연산

```javascript
console.log(Boolean(0n)); // false
console.log(Boolean(1n)); // true
console.log(Boolean(2n)); // true
```