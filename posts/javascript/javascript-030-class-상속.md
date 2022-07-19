# [JavaScript] class 상속

다른 언어의 클래스 상속과 마찬가지로 JavaScript에서도 클래스 상속을 할 수 있다.

## `extends`로 상속하기

```javascript
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }
  run(speed) {
    this.speed = speed;
    console.log(`${this.name} 은/는 속도 ${this.speed}로 달립니다.`);
  }
  stop() {
    this.speed = 0;
    console.log(`${this.name} 이/가 멈췄습니다.`);
  }
}

const animal = new Animal("동물");
```

이제 `extend` 키워드로 `Animal` 클래스를 상속받는 `Cat` 클래스를 만들어보자.

```javascript
class Cat extends Animal {
  jump() {
    console.log(`${this.name} 이/가 점프했습니다!`);
  }
}

const cat = new Cat("고양이");

cat.run(5); // 고양이 은/는 속도 5로 달립니다.
cat.stop(); // 고양이 이/가 멈췄습니다.
cat.jump(); // 고양이 이/가 점프했습니다!
```

이제 `Cat` 클래스로 생성한 객체는 `Animal` 클래스의 프로퍼티에 접근할 수 있다. 이는 `Cat.prototype.[[Prototype]]` 을 `Animal.prototype`으로 설정하기 때문에 가능하다.

## 메소드 오버라이딩

위 예처럼 `Cat` 클래스엔 `run`, `stop` 메소드, `name`, `speed` 변수가 없기 때문에 `Animal` 클래스의 프로퍼티를 참조해 동작한다. 즉, 호출한 변수, 메소드가 본 클래스에 없다면 프로토타입에서 해당 변수나 메소드를 찾는다.

반대로 메소드 오버라이딩을 하기 위해선 본 클래스에서 새로이 메소드를 생성해준다면 간단히 구현할 수 있다.

위 `Cat` 클래스를 아래와 같이 수정해보자.

```javascript
class Cat extends Animal {
  jump() {
    console.log(`${this.name} 이/가 점프했습니다!`);
  }

  run() {
    console.log(`${this.name} 이/가 울부짖습니다.`);
    super.run();
  }
}

const cat = new Cat("고양이");

cat.run(5); // 고양이 이/가 울부짖습니다. 고양이 은/는 속도 5로 달립니다.
```

`Cat` 클래스에서 `run` 메소드를 선언해주면 메소드 오버라이딩을 할 수 있다. 이 때, `super` 키워드로 부모 클래스의 `run` 메소드를 호출할 수 있다.

## 생성자 오버라이딩

생성자 메소드도 오버라이딩 할 수 있는데, 조건이 있다. 바로 `super()`를 가장 첫번째 줄에서 실행시켜줘야 한다.

```javascript
class Cat extends Animal {
  // INVALID
  constructor(name, isWild) {
    this.speed = 0;
    this.name = name;
    this.isWild = isWild;
  }

  // INVALID
  constructor(name, isWild) {
    this.isWild = isWild;
    super(name);
  }

  // VALID
  constructor(name, isWild) {
    super(name);
    this.isWild = isWild;
  }
}
```
