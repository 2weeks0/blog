# [JavaScript] 기본 연산자

- `자바스크립트`에서 사용할 수 있는 수학 연산자는 아래와 같다.
- 다른 언어와 비슷하여 헷갈릴만한 요소들만 정리해보자.

|기능|연산자|
|:--:|:--:|
|덧셈|`+`|
|뺼셈|`-`|
|곱셈|`*`|
|나눗셈|`/`|
|나머지|`%`|
|거듭제곱|`**`|



## `+` 연산자와 문자열

- `+` 연산자의 피연산자 중 하나가 `문자열`이면 `문자열 병합`을 한다.

```javascript
console.log(1 + "2") // "12"
console.log(1 + 1 + "2") // "22"
```

## 단항 연산자 `+`로 `숫자형`으로 변환

- `+` 를 단항 연산자로 사용하면 데이터를 `숫자형`으로 변환시켜준다.

```javascript
console.log(+"123") // 123
console.log(+true) // 1
console.log(+false) // 0
```

## 할당 연산자 `=`

- 변수에 값을 대입, 할당하는 연산자다.

### 값을 반환하는 `=` 연산자

- `자바`와 마찬가지로 값을 반환하기도 한다.

```javascript
let a = 1 // 1
let b = 2 // 2
let c = 3 - (a = b + 1) // 0
```

### 할당 연산자 체이닝

```javascript
let a, b, c
a = b = c = 1 + 1
console.log(a) // 2
console.log(b) // 2
console.log(c) // 2
```

### 복합 할당 연산자

- `a = a + 2`을 `a += 2` 로 표현할 수 있다.

```javascript
let a = 1
console.log(a) // 1
a *= 2
console.log(a) // 2
a *= 2
console.log(a) // 4
```

### 증감 연산자

- 변수의 앞/뒤에 ++, -- 해주면 +1, -1 된다.
- 변수의 앞에서 증감 연산자를 사용하면 그 즉시 증감 처리가 된다. (전위형)
- 변수의 뒤에서 증감 연산자를 사용하면 다음에 그 변수를 참조할 때, 증감 처리가 된 값을 반환한다. (후위형)

```javascript
let a = 1
console.log(a++) // 1
console.log(a) // 2
a = 1
console.log(++a) // 2
console.log(a) // 2
```

## 비트 연산자

|기능|연산자|
|:--:|:--:|
|AND|`&`|
|OR|`|`|
|XOR|`^`|
|NOT|`~`|
|왼쪽 시프트|`<<`|
|오른쪽 시프트|`>>`|
|부호 없는 오른쪽 시프트|`>>>`|


## 연산자 우선순위

- 자세한 우선순위는 아래 링크를 참고
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence
