# [JavaScript] Map

맵은 키가 있는 데이터를 저장하는 점에서 객체와 비슷하다. 하지만 객체와 다른 점은 맵에서의 키에는 문자열 뿐만 아니라 다양한 자료형을 가질 수 있다.

## 기본 메소드와 프로퍼티

- `new Map()`: 맵 객체를 생성한다.
- `map.set(key, value)`: key 값에 해당하는 value를 저장한다.
- `map.get(key`: key 값에 해당하는 value를 반환한다. 없다면 `undefined`를 반환한다.
- `map.has(key)`: key 값이 해당하는 value가 존재하면 `true`, 아니면 `false`를 반환한다.
- `map.delete(key)`: key 값에 해당하는 value를 삭제한다.
- `map.clear()`: 맵을 초기화한다.
- `map.size`: 저장되어 있는 요소의 개수를 반환한다.

```javascript
const map = new Map();

map.set(1, "num1");
map.set("1", "str1");
map.set(true, true)
    .set(null, null);
    
console.log(map.get(1)); // num1
console.log(map.get("1")); // str1
console.log(map.get(true)); // true
console.log(map.get(null)); // null
```

## 반복 작업

맵에서는 세 가지 메소드를 통해 각 요소에 반복 작업을 수행할 수 있다.

- `map.keys()`: 맵에 key 값들을 `iterable` 객체로 반환한다.
- `map.values()`: 맵에 value 값들을 `iterable` 객체로 반환한다.
- `map.entries()`: 맵에 [key, value] 를 갖는 객체들을 `iterable` 객체로 반환한다.

```javascript
const map = new Map([
    ["KIM", 170],
    ["LEE", 175],
    ["PARK", 180],
  ]);

  for (let key of map.keys()) {
    console.log(key);
  }
  // KIM
  // LEE
  // PARK

  for (let value of map.values()) {
    console.log(value);
  }
  // 170
  // 175
  // 180

  for (let entry of map.entries()) {
    console.log(entry);
  }
  //   [ 'KIM', 170 ]
  //   [ 'LEE', 175 ]
  //   [ 'PARK', 180 ]
```

`forEach` 구문을 사용할 수도 있다.

```javascript
forEach(callbackfn: (value: V, key: K, map: Map<K, V>) => void, thisArg?: any): void;
```

```javascript
const map = new Map([
    ["KIM", 170],
    ["LEE", 175],
    ["PARK", 180],
  ]);
  
map.forEach((value, key, map) => console.log(value, key, map));
// 170 KIM Map(3) { 'KIM' => 170, 'LEE' => 175, 'PARK' => 180 }
// 175 LEE Map(3) { 'KIM' => 170, 'LEE' => 175, 'PARK' => 180 }
// 180 PARK Map(3) { 'KIM' => 170, 'LEE' => 175, 'PARK' => 180 }
```

## 객체를 맵으로, 맵을 객체로

- `Object.entries`: 객체의 key-value 값을 쌍으로 갖는 배열을 반환한다.
- `Object.fromEntires`: 맵을 객체로 변환시켜 반환한다.

```javascript
 const obj = {
    name: "KIM",
    age: 30
};

const map = new Map(Object.entries(obj));
console.log(map); // Map(2) { 'name' => 'KIM', 'age' => 30 }

const obj2 = Object.fromEntries(map);
console.log(obj2); // { name: 'KIM', age: 30 }
```