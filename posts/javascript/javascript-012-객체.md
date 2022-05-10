# [JavaScript] 객체

- 자바스크립트 자료형엔 원시형(primitive type), 객체형이 있다. 원시형은 오직 하나의 데이터(문자, 숫자, 불린 등)을 담을 수 있지만 객체형은 다양한 데이터를 담을 수 있다.
- 객체에 "key: value" 쌍으로 구성된 프로퍼티를 넣어 여러 데이터를 담을 수 있다. 
- key에는 문자형, value엔 모든 자료형이 들어갈 수 있다.
- 객체를 만드는 방법은 아래처럼 2가지가 있다.

```javascript
let data1 = new Object() // `객체 생성자` 문법
let data2 = {}; // `객체 리터럴` 문법
```

- 주로 `객체 리터럴` 문법을 사용한다.

## 리터럴과 프로퍼티

```javascript
let data = {
    name: "Lee", // key: "name", value: "Lee"
    age: 30, // key: "age", value: 30
    "want to go home": true, // key: "want to go home", value: true
};
```

- 작성된 프로퍼티를 읽을 땐, 점 표기법이나 대괄호 표기법을 이용한다.

```javascript
console.log(data.name) // Lee
console.log(data.age) // 30
console.log(data.want to go home) // 불가능
console.log(data["want to go home"]) // key 값에 공백이 있을 경우엔 대괄호 표기법이 필수!!
```

- 추가는 아래와 같이 할 수 있다.

```javascript
data.isKorean = true // data["isKorean"] = true와 동일
```

- 삭제는 delete 연산자를 사용한다.

```javascript
delete data.age // delete data["age"]와 동일
```

## 대괄호 표기법
- 대괄호 표기법을 이용하면 동적으로 key 값을 불러올 수 있다.

```javascript
let data = {
    name: "Lee",
    age: 30,
};

let key = prompt("key 입력") // 만약 "name"이 입력되었다면
console.log(data[key]) // Lee
console.log(data.key) // undefined
```

- 동적으로 key 값을 할당할 수도 있다.
```javascript
let key = prompt("key 입력") // 만약 "name"이 입력되었다면

let data = {
    [key]: "Lee"
};

console.log(data.name); // Lee
```

## 단축 프로퍼티

- 프로퍼티 value에 변수 값을 넣을 때, key 값과 변수의 이름이 같다면 key를 생략하여 작성할 수 있다.

```javascript
let name = "LEE";
let age = 10;

let data = {
    name,
    age
};

console.log(data); // { name: 'LEE', age: 10 }
```

## `in` 연산자

- 자바스크립트에서는 존재하지 않는 프로퍼티에 접근하려고 해도 에러가 나지 않고, `undefined`를 반환한다.
- 이 때, `in` 연산자로 해당 프로퍼티가 존재하는지 확인할 수 있다.

```javascript
let name = "LEE";
let age = 10;

let data = {
    name,
    age,
};

console.log("name" in data); // true
console.log(name in data); // false, == console.log("LEE" in data)
```

## `for in` 반복문

- 객체 안에 key를 순회하는 반복문이다.

```javascript
let name = "LEE";
let age = 10;

let data = {
    name,
    age,
};

for (let key in data) {
    console.log(key, data[key]); // name "LEE" /n age 10
}
```

### 주의 사항
- key가 정수 프로퍼티일 경우, 자동 정렬이 된다.

```javascript
let data = {
    "3": "KIM",
    "2": "PARK",
    "1": "LEE"
};

for (let key in data) {
    console.log(key, data[key]);
}
```

- 위 경우, 선언은 3 "KIM"부터 했지만 출력은 1 "LEE" 부터 되는 걸 볼 수 있다.
- 이는 key가 정수 프로퍼티라 오름차순으로 정렬되어 발생한다.
- 이를 방지하기 위해선 key 앞에 + 를 붙여주면 된다.

```javascript
let data = {
    "+3": "KIM",
    "+2": "PARK",
    "+1": "LEE"
};

for (let key in data) {
    console.log(key, data[key]);
}
```