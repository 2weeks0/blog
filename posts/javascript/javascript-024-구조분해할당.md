# [JavaScript] 구조 분해 할당

객체나 배열을 변수로 분해하는 문법을 구조 분해 할당이라고 한다.

## 배열 분해하기

```javascript
let arr = ["apple", "banana"];

// 구조 분해 할당으로 
// first엔 arr[0], second엔 arr[1]을 할당
let [first, second] = arr;

console.log(first); // apple
console.log(second); // banana 
```

```javascript
let user = {
    name: "John",
    age: 30
};

for (let [key, value] of Object.entries(user)) {
    console.log(`${key}:${value}`);
}
// name:John
// age:30
```

### '...'로 나머지 요소 가져오기

...로 나머지 혹은 모든 요소를 모두 가져올 수 있다.

```javascript
let [first, second, ...rest] = ["apple", "banana", "peach", "pear"];

console.log(first); // apple
console.log(second); // banana

console.log(rest[0]); // peach
console.log(rest[1]); // pear
console.log(rest.length); // 2
```

### 기본값 설정하기

배열을 분해하여 값을 가져오다보면 변수의 개수가 배열의 길이보다 클 경우, 값을 가져오지 못해 `undefined` 값을 할당받게 된다.
이럴 때, 기본값 설정을 할 수 있다.

```javascript
let [first, second, third] = ["apple", "banana"];

console.log(first); // apple
console.log(second); // banana
console.log(third); // undefined

let [f, s, t = "unknown"] = ["apple", "banana"];

console.log(f); // apple
console.log(s); // banana
console.log(t); // unknown
```

## 객체 분해하기

객체에도 마찬가지로 적용할 수 있다.
다만, key 이름을 변수 이름으로 사용하면 쉽게 가져올 수 있다.

```javascript
let data = {
    name: "Lee",
    age: 30,
    address: "Seoul"
};

let { age, name, address, height } = data;

console.log(name); // Lee
console.log(age); // 30
console.log(address); // Seoul 
console.log(height); // undefined
```

변수 이름을 다르게 가져오고 싶다면, 아래와 같이 사용할 수 있다.

```javascript
let data = {
    name: "Lee",
    age: 30,
    address: "Seoul"
};

let { age: a, name: n } = data;

console.log(a); // 30
console.log(n); // Lee
```

### 기본값 설정하기

배열에서 분해했던 것과 마찬가지로 기본값을 줄 수 있다.

```javascript
let data = {
    name: "Lee",
    age: 30,
    address: "Seoul"
};

let { name, height = 180 } = data;

console.log(name); // Lee
console.log(height); // 180
```

### '...'로 나머지 요소 가져오기
```javascript
let data = {
    name: "Lee",
    age: 30,
    address: "Seoul"
};

let { name, ...rest } = data;

console.log(name); // Lee
console.log(rest); // { age: 30, address: 'Seoul' }
```