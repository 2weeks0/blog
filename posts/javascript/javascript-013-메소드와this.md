# [JavaScript] 메소드와 `this`

## 메소드 만들기

- 객체 안에 메서드를 생성해보자.
```javascript
let data = {
    name: "LEE",
    sayName() {
        console.log("sayName");
    }
};

data.sayName(); // sayName
```

## 메소드와 `this`

- 객체 안에 메소드를 생성할 때는 객체 안에 데이터에 사용하기 위함일 것이다.
- 위에 `sayName` 메소드에서 실제 데이터인 `name`을 이용해 메소드를 완성시켜보자.

```javascript
let data = {
    name: "LEE",
    sayName() {
        console.log(`sayName - ${this.name}`);
    }
};

data.sayName(); // sayName - LEE
```

## `this`와 런타임

- 다른 언어와 `this` 동작 방식이 다르다.
- `this`의 값이 런타임에 결정된다.

```javascript
let dataA = {
    name: "dataA",
    sayName,
};
let dataB = {
    name: "dataB",
    sayName,
};

function sayName() {
    console.log(this.name);
}

dataA.sayName(); // dataA
dataB.sayName(); // dataB
sayName(); // undefined
```

## `this`가 없는 화살표 함수

- 화살표 함수에서는 `this`를 갖지 않는다.
- 따라서, 화살표 함수에서 `this`를 호출하면 화살표 함수가 아닌 외부 함수에서 `this` 값을 갖고 온다.

```javascript
let name = "name";
let data = {
    name: "data",
    sayName: () => {
        console.log(this.name);
    }   
};

data.sayName(); // undefined
```