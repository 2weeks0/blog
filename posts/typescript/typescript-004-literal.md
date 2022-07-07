# [TypeScript] 리터럴 타입

TypeScript에는 문자열과 숫자 두 가지 리터럴 타입이 있다. 이를 사용하면 정확한 문자열이나 숫자 값을 지정할 수 있다.

## 문자열 리터럴 타입

문자열로 리터럴 타입을 지정할 수 있다. 마치 enum 처럼 사용할 수 있다.

```typescript
type Drink = "water" | "coffee" | "beer";

function action(drink: Drink) {
  if (drink === "water") {
  } else if (drink === "coffee") {
  } else if (drink === "beer") {
  } else {
    // 도달할 수 없음!!
  }
}
```

## 숫자 리터럴 타입

숫자 리터럴 타입을 통해 number의 구체적 범위나 값을 정할 수 있다.

```typescript
type DiceValue = 1 | 2 | 3 | 4 | 5 | 6;

function rollDice(): DiceValue {
  return (Math.floor(Math.random() * 6) + 1) as DiceValue;
}
```
