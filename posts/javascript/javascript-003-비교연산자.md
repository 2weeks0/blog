# [JavaScript] 비교/일치 연산자
- `자바`와 거의 유사하나 조금 다른 것이 있다. 천천히 살펴보자.

## 비교 연산자

### 불린형 반환
```javascript
console.log(4 < 5) // true
var value = 4 != 4
console.log(value) // false
```

### 문자열 비교
- 사전 순으로 문자열을 비교한다.

```javascript
console.log('AAA' < 'AAB') // true
console.log('AAA' < 'AAAA') // true
console.log('a' < 'A') // false -> 'a' 유니코드가 'A'보다 크다
```

- 문자열을 비교하는 알고리즘 아래와 같다.
1. 두 문자열의 첫 글자를 비교한다.
2. 첫 번째 문자열의 첫 글자가 다른 문자열의 첫 글자보다 크면(작으면), 첫 번째 문자열이 두 번째 문자열보다 크다고(작다고) 결론 내고 비교를 종료한다.
3. 두 문자열의 첫 글자가 같으면 두 번째 글자를 1, 2번 방식으로 비교한다.
3. 글자 간 비교가 끝날 때까지 이 과정을 반복한다.
4. 비교가 종료되었고 문자열의 길이도 같다면 두 문자열은 동일하다고 결론낸다.. 비교가 종료되었지만 두 문자열의 길이가 다르면 길이가 긴 문자열이 더 크다고 결론낸다.

### 서로 다른 형태의 값 비교
- 비교하려는 값의 자료형이 다르면 `숫자형`으로 바꿔 비교한다.

```javascript
console.log('12' < 123) // true
console.log('05' == 5) // true
console.log(true == 1) // true
console.log(false == 1) // false
```

## 일치 연산자
- `==` 연산자로는 `true`와 `1`을 구별하지 못한다. 이 경우 일치 연산자인 `===` 연산자로 구별할 수 있다.

```javascript
console.log(true == 1) // true
console.log(true === 1) // false
```

## `null`, `undefined` 와 연산자
- `null`과 `undefined` 는 일치하지 않지만 동등 연산자 `==`로 비교하면 `true`가 나온다.

```javascript
console.log(null === undefined) // false
console.log(null == undefined) // true
```

### `null`과 `0` 비교
```javascript
console.log(null > 0) // false
console.log(null == 0) // false
console.log(null >= 0) // true
```

- 비교 연산자 `<=`와 동등 연산자 `==`와 동작 방식이 다르다.
  - 비교 연산자는 숫자로 변환하여 동작하기 때문에 `null`이 `0`으로 변환된다.
  - 하지만 `null`에 동등 연산자 `==`로 비교하여 `true`를 얻기 위해선 `null`이나 `undefined`와 비교해주어야 하기 때문에 `0`와 비교하면 `false`가 나온다.


### `undefined`와 `0` 비교
```javascript
console.log(undefined > 0) // false
console.log(undefined == 0) // false
console.log(undefined >= 0) // false
```

- `undefined`는 `null`과 유사하나 비교할 때, `NaN` 값으로 반환되기 때문에 위와 같은 결과가 나온다.
