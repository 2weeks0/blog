# [JavaScript] Set

셋은 중복을 허용하지 않는 컬렉션이다.

## 기본 메소드와 프로퍼티

- `new Set()`: 셋 객체를 생성한다.
- `set.add(value)`: value를 추가하고 셋 자신을 반환한다. (체이닝 가능)
- `set.delete(value)`: value를 제거하고, 제거 전 해당 value가 셋에 포함되어 있었다면 `true`, 아니면 `false`를 반환한다.
- `set.has(value)`: value가 존재하면 `true`, 아니면 `false`를 반환한다.
- `set.clead()`: 셋을 초기화한다.
- `set.size`: 셋의 요소 개수를 반환한다.

```javascript
const set = new Set();

set.add(1);
set.add(2);
set.add(3)
    .add(1);

console.log(set); // Set(3) { 1, 2, 3 }
```

## 반복 작업

맵에서는 세 가지 메소드를 통해 각 요소에 반복 작업을 수행할 수 있다.

- `set.keys()`: `set.values()`와 동일. 맵과 호환을 위해 존재한다.
- `set.values()`: 셋 내의 모든 값들을 `iterable` 객체로 반환한다.
- `set.entries()`: 셋 내의 value로 [value, value] 를 갖는 객체들을 `iterable` 객체로 반환한다. 맵과 호환을 위해 존재한다.

```javascript
const set = new Set(["KIM", "LEE", "PARK",]);

for (let key of set.keys()) {
    console.log(key);
}
// KIM
// LEE
// PARK

for (let value of set.values()) {
    console.log(value);
}
// KIM
// LEE
// PARK

for (let entry of set.entries()) {
    console.log(entry);
}
// [ 'KIM', 'KIM' ]
// [ 'LEE', 'LEE' ]
// [ 'PARK', 'PARK' ]
```
