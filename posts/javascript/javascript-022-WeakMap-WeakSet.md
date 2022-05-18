# [JavaScript] WeakMap과 WeakSet

## WeakMap 이란?

자바스크립트에선 `가비지 컬렉션`을 통해 더 이상 사용되지 않는 객체들을 메모리에서 지워나간다.
이 때, 자료구조에 속한 객체들은 가비지 컬렉션의 대상에서 제외되는데, WeakMap과 WeakSet을 이용하면 약간 연결 관계를 지속할 수 있다.

```javascript
let data = { name: "LEE" };
let map = new Map();
map.set(data, "data");

data = null;

console.log(map.size);
```

위 코드에서 data를 null로 바꾸었음에도 불구하고 map에는 이전 data가 살아있다. 따라서, 가비지 컬렉션의 대상이 되지 않는다.

```javascript
let data = { name: "LEE" };
let map = new WeakMap();
map.set(data, "data");

data = null; // map 에 data 객체가 사라짐!!
```

WeakMap을 사용하면 data 객체가 null로 할당되는 시점에 WeakMap에서도 삭제된다.
따라서, WeakMap에는 객체만 key 값으로 올 수 있고, 지원하는 메소드도 적다.

### WeakMap 메소드

- `new WeakMap()`
- `weakMap.get(key)`
- `weakMap.set(key, value)`
- `weakMap.delete(key)`
- `weakMap.has(key)`

가비지 컬렉션이 동작하는 시점을 캐치할 수 없기 때문에, 최소한의 메소드만을 지원한다.


## WeakSet 이란?

WeakSet은 WeakMap의 Set 버전이다. 동작 방식은 WeakMap과 유사하다.

### WeakSet 메소드

- `new WeakSet()`
- `weakSet.add(value)`
- `weakSet.delete(value)`
- `weakSet.has(value)`