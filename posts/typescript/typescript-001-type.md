# [TypeScript] Type

## Boolean

JavaScript의 `boolean`과 같다. 참/거짓(true/false)을 갖는다.

```typescript
let isDone: boolean = false;
isDone = true;
```

## Number

JavaScript처럼 TypeScript의 모든 숫자는 부동 소수 값이다.

```typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

## String

JavaScript처럼 작은 따옴표, 큰 따옴표 또는 백틱을 사용해 문자열 데이터를 감싸면 된다.

```typescript
let string1: string = "hi";
let string2: string = 'hi';
let string3: string = `hi ${string1}`;
```

## Array

배열 타입은 두 가지 방법으로 쓸 수 있다.

```typescript
let arr: number[] = [1, 2, 3];
let arr2: Array<number> = [1, 2, 3];
```

## Tuple

튜플 타입은 요소의 타입과 개수가 고정된 배열을 뜻한다.

```typescript
let tuple: [string, number];

x = ["hi", 1]; // 올바른 초기화
x = [1, "hi"]; // 잘못된 초기화 - 에러 발생
```

## Enum

타 언어의 enum과 같다.

```typescript
enum Color {Red, Green, Blue}
let color: Color = Color.Green;
let green: Color = Color[1];
```

enum에선 첫번째 요소가 0번째 인덱스를 갖도록 설정되어있다. 예제처럼 1번째 인덱스를 참조하여 Green 값을 참조할 수 있다. 상황에 따라선 인덱스 값을 변경할 수도 있다.

```typescript
enum Color {Red = 1, Green, Blue}
let red: Color = Color[1];
let green: Color = Color[2];
```

## Any

알지 못하는 타입을 다룰 때, any를 쓸 수 있다.

```typescript
let value = "value";
value = false;
```

## void

아무 타입도 존재하지 않을 때, 사용한다. any의 반대 표현과 같다.

```typescript
function print(msg: string): void {
    console.log(msg);
}
```

## Null과 Undefined

null과 undefined는 value와 type이 같다. 필요충분조건이다.

```typescript
let n: null = null;
let u: undefined = undefined;
```


## Never

절대 발생할 수 없는 타입을 never라고 한다. 주로 함수 내에서 throw로 예외를 발생시키거나, 무한 루프를 탈 때, 위 타입을 사용할 수 있다.

```javascript
function error(msg: string): never {
    throw new Error(message);
}

function infiniteLoop(): never {
    while (true) {
    }
}
```

## Object

primative 타입을 제외한 모든 타입이 object 타입이다. JSON 객체를 말한다.

```typescript
let obj: object = {
    name: "LEE",
    age: 30,
};
```

## Type Assertions

다른 언어의 타입 변환과 비슷하지만 런타임에 영향을 끼치는 게 아닌, 컴파일러 단에서 처리한다. 사용 방법엔 두 가지가 있다.

1. angle-bracket

```typescript
const value: any = "value";
const length: number = (<string>value).length;
```

2. as

```typescript
const value: any = "value";
const length: number = (value as string).length;
```