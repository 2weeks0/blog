# [TypeScript] interface

## interface란?

TypeScript의 interface는 Java와 interface와 유사하다. 새로운 타입을 만들고, 해당 타입의 프로퍼티의 타입과 변수 이름을 정해놓은 설명서라고 보면 된다.

```typescript
interface ITest {
    name: string;
}

function print(testObj: ITest) {
    console.log(testObj.name);
}

const test = { name: "LEE" };
print(test);
```

위 예처럼 interface와 동일한 형태의 객체 뿐만 아니라 interface를 포함하는 객체도 허용된다.

```typescript
interface ITest {
    name: string;
}

function print(testObj: ITest) {
    console.log(testObj.name);
}

const test = { name: "LEE", age: 20 };
print(test);
```

## Optional Properties

es6 문법중에 Optional Chaining이라는 문법이 있다. null이거나 undefined 일 수 있는 변수를 참조할 때, 뒤에 `?`를 붙여 사용하는 문법이다. interface에도 유사한 문법이 있다. 해당 변수가 있을 수도, 없을 수도 있을 때 사용한다.

```typescript
interface ITest {
    name: string;
    age?: number;
}
```

## Readonly properties

const 와 같은 개념이다.

```typescript
interface ITest {
    readonly name: string;
    readonly age: number;
}

const test: ITest = { name: "LEE", age: 20 };
test.age = 10; // 에러!!
```

## 함수 타입

interface로 함수 선언?도 할 수 있다.

```typescript
interface MyFunc {
    (str1: string, str2: string): boolean;
}

const func: MyFunc = function(s1: string, s2: string) {
    return s1 === s2;
}
```

매개변수의 이름은 달라도 되고, 타입을 생략할 수도 있다.

```typescript
const func: MyFunc = function(s1, s2) {
    return s1 === s2;
}
```