# [JavaScript] 정적 메소드와 정적 프로퍼티

프로토타입이 아닌 클래스 함수 자체에 메소드나 프로퍼티를 설정할 수 있다. 이를 정적(static) 메소드/프로퍼티라고 한다.

## 정적 메소드

```javascript
class Student {
  static staticMethod() {
    console.log("staticMethod");
  }
}

Student.staticMethod(); // staticMethod
```

위 처럼 클래스 내부에서 `static` 메소드를 정의하는 행위는 아래처럼 프로퍼티에 직접 할당하는 것과 같다.

```javascript
class Student {
  static staticMethod() {
    console.log("staticMethod");
  }
}

Student.staticMethod = () => console.log("asd");

Student.staticMethod(); // asd
```

## 정적 프로퍼티

정적 프로퍼티도 마찬가지로 정적 메소드처럼 사용할 수 있다.

```javascript
class Student {
  static staticProperty = "staticProperty";
}

console.log(Student.staticProperty); // staticProperty
```

## 정적 메소드/프로퍼티 상속

정적 메소드/프로퍼티도 클래스 메소드/프로퍼티처럼 상속이 가능하다.

```javascript
class Student {
  static staticProperty = "staticProperty";
}

class HighSchoolStudent extends Student {

}

console.log(HighSchoolStudent.staticProperty); // staticProperty
```