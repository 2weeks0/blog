# [TypeScript] 함수

TypeScript의 함수에선 인자의 타입과 리턴값의 타입을 명시해줄 수 있다.

```typescript
function add(a: number, b: number): number {
    return a + b;
}

const addArrorw = (a: number, b: number): number => (a + b);
```

## Optional Parameter

함수를 작성하면서 파라메타를 선택적으로 받고 싶을 경우가 있을 때가 있다. 이 때 interface 처럼 뒤에 `?`를 붙여주면 된다.

```typescript
function add(a: number, b: number, c?: number): number {
    if (c) {
        return a + b + c;
    }
    return a + b;
}

console.log(add(1)); // 에러, 파라메타가 적음
console.log(add(1, 2)); // 성공, 3
console.log(add(1, 2, 3)); // 성공, 6
```

## Default Parameter

JavaScript와 마찬가지로 파라메타의 기본값을 줄 수 있다.

```typescript
function add(a: number, b: number, c: number = 3): number {
    return a + b + c;
}

console.log(add(1)); // 에러, 파라메타가 적음
console.log(add(1, 2)); // 성공, 6
console.log(add(1, 2, 3)); // 성공, 6
```

## Rest Parameters

JavaScript 함수의 나머지 매개변수 문법을 사용할 때도 타입을 넣어줄 수 있다. 이 땐 array 타입으로 넣어줘야 한다.

```typescript
function add(...nums: number[]): number {
    return nums.reduce((sum, cur) => (sum + cur));
}

console.log(add(1)); // 1
console.log(add(1, 2)); // 3
console.log(add(1, 2, 3)); // 6
```