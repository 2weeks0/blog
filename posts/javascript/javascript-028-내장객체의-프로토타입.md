# [JavaScript] 내장 객체의 프로토타입

`prototype` 프로퍼티를 이용한 프로토타입 상속은 우리가 자주 사용하는 Object, Array 객체 등에서 사용된다. Java로 따지면 모든 `class`가 `Object class`를 상속받는 것처럼 말이다.

## Object.prototype

```javascript
const obj = {};
console.log(obj); // [object Object]
```

위 예제를 실행하면 `[object Object]`이 출력된다. 우리가 만든 `obj`는 빈 객체지만 `toString` 메소드가 실행되어 log가 찍히는 것이다. 사실 `toString` 메소드는 이는 `Object.prototype`에서 가져오는 것이다. 이를 확인해보자.


```javascript
const obj = {};

console.log(obj.__proto__ === Object.prototype); // true
console.log(obj.toString === obj.__proto__.toString); //true
console.log(obj.toString === Object.prototype.toString); //true
```

## Array.prototype

이번엔 `Array` 객체를 살펴보자.

```javascript
const arr = [];

console.log(arr.__proto__ === Array.prototype); // true
console.log(arr.__proto__.__proto__ === Object.prototype); //true
console.log(arr.toString === Object.prototype.toString); //true
```

생성된 `arr` 객체의 `prototype` 프로퍼티는 `Array.prototype`을 가리키고, `Array`의 `prototype` 프로퍼티는 `Object.prototype`를 가리킨다. 따라서, `arr`의 `toString` 메소드는 `Object.prototype.toString`을 가리키게 된다.

## 원시값의 prototype

원시값인 문자열, 숫자, 불린 값은 객체가 아니다. 하지만 원시 타입 값의 프로퍼티에 접근할 때, 래퍼 객체가 생성되어 메소드를 제공하게 된다. 따라서 원시값을 다룰 때도, 객체의 프로토타입을 다루듯이 사용할 수 있게 된다.