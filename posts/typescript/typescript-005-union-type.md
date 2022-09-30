# [TypeScript] 유니언 타입 (Union Types)

## 유니언 타입이란?

아래와 같은 함수가 있다고 하자.

```typescript
/**
 * 문자열을 받고 왼쪽에 "padding"을 추가합니다.
 * 만약 'padding'이 문자열이라면, 'padding'은 왼쪽에 더해질 것입니다.
 * 만약 'padding'이 숫자라면, 그 숫자만큼의 공백이 왼쪽에 더해질 것입니다.
 */
function padLeft(value: string, padding: any) {
  if (typeof padding === "number") {
    return Array(padding + 1).join(" ") + value;
  }
  if (typeof padding === "string") {
    return padding + value;
  }
  throw new Error(`Expected string or number, got '${padding}'.`);
}

padLeft("Hello world", 4); // "Hello world"를 반환합니다.
```

위 `padLeft` 함수에 `padding` 인자는 문자열 또는 숫자 타입의 파라미터를 받길 원한다.

이 때, `유니언 타입`이 쓰인다. `유니언 타입`은 서로 다른 타입의 값 중 하나의 타입을 허용할 때 사용한다.

`유니언 타입`을 적용하여 `padLeft` 함수를 다시 작성해보면 아래와 같다.

```typescript
function padLeft(value: string, padding: string | number) {
  // ...
}
```

## 공통 필드를 갖는 유니언

`유니언 타입`의 변수가 유니언에 있는 모든 타입의 공통인 멤버에 접근할 수 있다.

```typescript
interface Bird {
  fly(): void;
  layEggs(): void;
}

interface Fish {
  swim(): void;
  layEggs(): void;
}

declare function getSmallPet(): Fish | Bird;

let pet = getSmallPet();
pet.layEggs();

// 두 개의 잠재적인 타입 중 하나에서만 사용할 수 있습니다.
pet.swim();
```

`Bird`와 `Fish` 타입엔 공통적으로 `layEggs` 멤버가 있기 때문에 유니언 타입인 `getSmallPet()`에서 `layEggs`를 참조할 수 있다.

하지만 각 타입만이 갖고 있는 멤버에 접근할 땐, 에러가 발생한다.

## 유니언 구별하기

```typescript
type NetworkLoadingState = {
  state: "loading";
};

type NetworkFailedState = {
  state: "failed";
  code: number;
};

type NetworkSuccessState = {
  state: "success";
  response: {
    title: string;
    duration: number;
    summary: string;
  };
};

type NetworkState =
  | NetworkLoadingState
  | NetworkFailedState
  | NetworkSuccessState;

function networkStatus(state: NetworkState): string {
  // 현재 TypeScript는 셋 중 어떤 것이
  // state가 될 수 있는 잠재적인 타입인지 알 수 없습니다.

  // 모든 타입에 공유되지 않는 프로퍼티에 접근하려는 시도는
  // 오류를 발생시킵니다.
  state.code;

  // state에 swtich문을 사용하여, TypeScript는 코드 흐름을 분석하면서
  // 유니언 타입을 좁혀나갈 수 있습니다.
  switch (state.state) {
    case "loading":
      return "Downloading...";
    case "failed":
      // 여기서 타입은 NetworkFailedState일 것이며,
      // 따라서 `code` 필드에 접근할 수 있습니다.
      return `Error ${state.code} downloading`;
    case "success":
      return `Downloaded ${state.response.title} - ${state.response.summary}`;
  }
}
```

`NetworkState` 타입 내 공통 멤버인 `state`를 이용해 switch문을 작성한 예제다.

`state`는 리터럴 타입의 값이기 때문에 switch 문을 사용해 범위를 좁혀 코드를 작성할 수 있다.