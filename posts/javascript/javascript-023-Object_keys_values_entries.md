# [JavaScript] Object.keys, values, entries

## Object.keys, values, entries

위 메소드들을 통해 일반 객체에서도 key, value, [key, value]를 순회할 수 있다.
- `Object.keys(obj)`: 객체의 key만 담은 배열을 반환한다.
- `Object.values(obj)`: 객체의 value만 담은 배열을 반환한다.
- `Object.entries(obj)`: 객체의 [key, value]를 담은 배열을 반환한다.

```javascript
const data = {
    name: "LEE",
    age: "30"
};

console.log(Object.keys(data)); // [ 'name', 'age' ]
console.log(Object.values(data)); // [ 'LEE', '30' ]
console.log(Object.entries(data)); // [ [ 'name', 'LEE' ], [ 'age', '30' ] ]
```

## 객체로 변환

객체엔 `map`, `filter` 같은 배열에서 사용하던 메소드를 사용할 수 없다.
이 때, 앞서 언급한 `Object.entries(obj)` 메소드를 이용해 작업할 수 있다.

```javascript
const data = {
    apple: 1000,
    banana: 3000,
    pear: 5000,
};

const data2 = Object.fromEntries(
    Object.entries(data).map(([fruit, price]) => [fruit, 2 * price])
);
console.log(data2); // { apple: 2000, banana: 6000, pear: 10000 }
```