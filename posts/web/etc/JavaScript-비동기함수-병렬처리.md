# [JavaScript] 비동기 함수 병렬 처리

## 개요

프로그래밍에서 일반적인 함수는 직렬로 실행된다.
즉, 현재 라인의 처리가 끝난 후, 다음 라인으로 넘어간다는 것이다.
이를 동기(Synchronous)라고 한다. 하지만 네트워크 작업 등 언제 끝날지 모르거나 오래 걸리는 작업의 경우 동기적으로 진행하면 그 동안 다른 작업을 수행하지 못해 손해가 발생한다.
이 때, 비동기(Asynchronous) 작업으로 유연하게 처리할 수 있다.

비동기로 함수를 작성할 때도 병렬로 처리해주어야 앞서 언급한 다른 작업을 수행하지 못하는 문제가 발생하지 않는다.
아래과 같은 비동기 함수가 있다고 해보자.

|함수|걸리는 시간|
|:---:|:---:|
|A|300ms|
|B|200ms|
|C|100ms|

```javascript
const delay = { A: 300, B: 200, C: 100 };

function request(type) {
  return new Promise((resolve) => {
    setTimeout(function () {
      resolve(type);
    }, delay[type]);
  });
}
```

함수 A, B, C는 독립적으로 실행할 수 있으며 순차적으로 실행하고자 한다.
이를 병렬로 처리한다면 모든 함수가 끝나는 데 걸리는 데 300ms 시간이 걸릴 것이다.
(시간 소요는 비동기 함수에서만 발생한다고 가정.)
하지만 직렬로 처리하게 되면 `600ms`의 시간이 걸린다.
따라서 비동기 함수도 상황에 맞게 병렬로 처리해주어야만 효과적인 프로그래밍이 가능하다.

---

JavaScript의 Promise로 비동기 프로그래밍을 해보자.

직렬, 병렬, 병렬-순서보장 순으로 진행할 것이다.

## Promise - 직렬

```javascript
request('A').then((response) => {
    console.log(response);
    request('B').then((response) => {
        console.log(response);
        request('C').then((response) => {
            console.log(response);
        });
    });
});
```

>출력결과  
>A  
>B  
>C

직렬로 실행했기 때문에 대략 `600ms` 의 시간이 걸리고, A, B, C의 결과가 순차적으로 출력되었다.

## Promise - 병렬

```javascript
request('A').then((response) => console.log(response));
request('B').then((response) => console.log(response));
request('C').then((response) => console.log(response));
```

>출력결과  
>C  
>B  
>A

병렬로 처리하면 먼저 끝나는 C부터 B, A 순으로 출력된다.
이 때, 대략 `300ms` 시간이 걸린다.

## Promise - 병렬 순서보장

만약, 함수 A, B, C가 순서가 보장되어야하는 상황이라면 어떻게 해야할까?
직렬로 처리하면 순서를 보장할 수 있지만 시간 손해가 발생한다.
이럴 땐, 병렬로 처리하되 그 결과를 순서대로 받는다면 순서가 보장되고, 시간 손해가 발생하지 않는다.

```javascript
const requestList = [
    request('A'),
    request('B'),
    request('C'),
];

Promise.all(requestList).then((responses) => {
    for (const response of responses) {
        console.log(response);
    }
});
```

>출력결과  
>A  
>B  
>C

출력 결과는 직렬과 같지만 대략 `300ms`의 시간이 걸린다는 점이 직렬 방식과 다르다.

---
이제 async/await 방식으로 구현해보자.
문법만 다를 뿐, 실행 결과나 성능은 앞선 방식과 차이가 없다.

마찬가지로 직렬, 병렬, 병렬-순서보장 순으로 진행할 것이다.

## async/await - 직렬

```javascript
console.log(await request('A'));
console.log(await request('B'));
console.log(await request('C'));
```

>출력결과  
>A  
>B  
>C

## async/await - 병렬

```javascript
const arr = ["A", "B", "C"];
arr.forEach(async (type) => console.log(await request(type)));
```

>출력결과  
>C  
>B  
>A

## async/await - 병렬 순서보장

```javascript
const arr = ["A", "B", "C"];
const arrFunc = arr.map((type) => request(type));

for (const func of arrFunc) {
    console.log(await func);
}
```

>출력결과  
>A  
>B  
>C