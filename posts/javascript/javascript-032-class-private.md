# [JavaScript] private 메소드/프로퍼티

캡슐화는 객체 지향 프로그래밍에서 중요한 개념이다. 캡슐화된 클래스에서는 메소드를 프로퍼티를 두 그룹으로 분류하여 사용한다.

- 내부 인터페이스: 클래스 내에서는 접근할 수 있지만, 클래스 밖에서는 접근할 수 없는 메소드와 프로퍼티

- 외부 인터페이스: 클래스 안, 밖에서 모두 접근할 수 있는 메소드와 프로퍼티

내부 인터페이스를 `private`라 하고, 외부 인터페이스를 `public`이라고 한다. 참고로 `private`와 `public` 사이의 개념인 `protected`도 있는데, 이는 내부, 자손 클래스에서 사용 가능한 개념이다.


## 프로퍼티 보호하기

```javascript
class Student {
  score = 0; 

  constructor(score) {
    this.score = score;
  }

}

const student = new Student(-10);

console.log(student.score); // -10
```

위 클래스는 학생 클래스이고, `score`라는 프로퍼티를 갖는다. 하지만 실생활에서 점수가 음수를 가질 수 없으므로 아래와 같이 안전하게 사용할 수 있게 변경할 수 있다.

```javascript
class Student {
  constructor(score) {
    this.score = score;
  }

  set score(score) {
    if (score < 0) {
        throw new Error("점수는 음수가 될 수 없습니다.");
    }
    this._score = score;
  }

  get score() {
    return this._score;
  }
}

const student = new Student(-10); // Error: 점수는 음수가 될 수 없습니다.
```

## `private` 메소드/프로퍼티

`private` 메소드나 프로퍼티를 생성하기 위해선 변수명 앞에 `#`을 붙여주면 된다.

```javascript
class Student {
  #score = 0;

  constructor(score) {
    this.score = score;
  }

  set score(score) {
    if (score < 0) {
        throw new Error("점수는 음수가 될 수 없습니다.");
    }
    this.#score = score;
  }

  get score() {
    return this.#score;
  }
}

const student = new Student(10);

console.log(student.score); // 10
console.log(student["#score"]); // undefined
```

`private`를 사용하면 원래 변수를 밖에서 접근할 수 없도록 할 수 있다. 오직 `setter`, `getter`로만 접근할 수 있다.