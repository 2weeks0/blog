# [JavaScript] 프로토타입

## `[[ProtoType]]`

JavaScript의 객체는 `[[ProtoType]]` 이라는 숨김 프로퍼티를 갖고 있다. 이 `[[ProtoType]]` 프로퍼티에 다른 객체를 참조하여 해당 객체의 변수와 기능을 가질 수 있다. 이게 왜 중요한가라는 의문이 생길 수 있다. 굳이 `[[ProtoType]]` 프로퍼티를 이용하지 않아도 다른 객체를 참조하는 프로퍼티를 얼마든지 만들 수 있기 때문이다.

하지만 JavaScript의 `[[ProtoType]]` 프로퍼티를 활용하는 방식을 보면 의미를 찾을 수 있다. JavaScript는 객체에서 어떤 프로퍼티를 읽을 때, 해당 객체에 그 프로퍼티가 없으면 `[[ProtoType]]` 프로퍼티에서 찾는다. 이러한 동작 방식 덕분에 `[[ProtoType]]`을 활용해 `상속`받은 것 처럼 동작하게 할 수 있다. 이를 `프로토타입 상속`이라고 한다.

`[[ProtoType]]`의 get, set은 `__proto__`로 할 수 있다.

```javascript
const human = {
  walk: "walk",
};
const student = {
  study: "study",
};

student.__proto__ = human;

console.log(student.walk); // walk
```

`student` 객체엔 `walk`라는 프로퍼티가 없음에도 불구하고 정상적으로 실행이 되는 모습이다. 이는 `walk`라는 프로퍼티를 프로토타입 프로퍼티에서 찾아 `human` 객체의 `walk`라는 프로퍼티를 참조하게 된다.

마치 상속을 받은 것처럼 보인다.

앞선 예제 코드는 아래처럼 쓸 수도 있다.

```javascript
const human = {
  walk: "walk",
};
const student = {
  study: "study",
  __proto__: human,
};

console.log(student.walk); // walk
```

## 프로토타입은 읽기 전용

프로토타입은 읽기 전용이다. 즉, 프로퍼티를 추가, 수정, 삭제를 할 땐, 객체에 직접 해줘야 한다.

```javascript
const human = {
  walk: "walk",
};
const student = {
  study: "study",
  __proto__: human,
};

student.walk = "walk!!";
console.log(student.walk); // walk!!
console.log(human.walk); // walk
```

`student` 객체의 `walk` 프로퍼티에 `walk!!` 값을 추가하는 결과를 볼 수 있다. 즉, `human` 객체의 `walk` 프로퍼티와 관련 없는 `student` 객체의 새로운 프로퍼티가 되는 것이다.

## `for in`

`for in`에선 프로토타입의 프로퍼티도 순회한다.

```javascript
const human = {
  walk: "walk",
};
const student = {
  study: "study",
  __proto__: human,
};

for (const prop in student) {
  console.log(prop, student.hasOwnProperty(prop)); //study true walk false
}

console.log(Object.keys(student)); // [ 'study' ]
```

반면에 `Object.keys(obj)` 메소드에선 프로토타입을 제외한 프로퍼티만을 참조한다. 또, `obj.hasOwnProperty(prop)` 메소드를 통해 상속 프로퍼티를 걸러낼 수 있다.

