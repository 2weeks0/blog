# [JavaScript] 클래스

## 클래스란

다른 언어와 다르게 JavaScript에서 클래스란 함수의 한 종류다.

```javascript
class Student {
  constructor(name) {
    this.name = name;
  }

  sayName() {
    console.log(this.name);
  }
}

console.log(typeof Student); // function
```

클래스의 문법은 아래와 같이 동작한다.

1. `Student`라는 이름의 함수를 만든다. 함수 본문은 생성자 메소드인 `constructor`에서 가져온다.
2. 클래스 내에 정의된 메소드 `sayName`을 `Student.prototype`에 저장한다.

위 내용들을 코드로 확인하면 아래와 같다.

```javascript
class Student {
  constructor(name) {
    this.name = name;
  }

  sayName() {
    console.log(this.name);
  }
}

console.log(typeof Student); // function
console.log(Student === Student.prototype.constructor); // true
console.log(Student.prototype.sayName); // console.log(this.name);
```

## 클래스와 함수의 차이점

클래스는 함수와 같은 것으로 생각할 수 있지만 차이점이 있다.

1. 클래스는 내부 프로퍼티로 `IsClassConstructor`를 `true` 값으로 갖는다. 이 프로퍼티로 함수와 클래스를 구분하는데, 함수는 `new` 키워드 없이 실행할 수 있는 반면에 클래스는 `new` 없이 실행하면 에러가 난다.

```javascript
function TestFunc() {
  console.log("TestFunc");
}
TestFunc();

class TestClass {
  constructor() {
    console.log("TestClass");
  }
}

TestClass(); // Uncaught TypeError: Class constructor TestClass cannot be invoked without 'new'
```

2. 클래스에 정의된 메소드는 열거할 수 없다. (non-enumerable) 클래스에서 메소드에 의해 추가된 프로토타입 프로퍼티는 모두 `enumerable = false`다.

## getter / setter

```javascript
class Student {
  #name;

  constructor(name) {
    this.name = name;
  }

  get name() {
    return this.#name;
  }

  set name(value) {
    if (!value) {
      console.log("이름을 입력해주세요");
      return;
    }
    this.#name = value;
  }

  sayName() {
    console.log(this.name);
  }
}

let student = new Student("학생");
student.sayName(); // 학생

student = new Student(""); // 이름을 입력해주세요
```

생성자에서 `this.name = name` 구문에 `setter`가 동작하는 걸 확인할 수 있다. 이 때, `setter`에서 `this.name = value`라고 하면 무한 루프에 빠지기 때문에 변수 앞에 #을 붙여 private 속성을 부여해준다.

(es2022 문법에서 클래스에 private 변수를 사용할 수 있게 되었다.)
