# Collection을 사용한 분기 처리

일반적으로 if/else-if나 switch 구문을 통해 분기 처리를 한다.
하지만 가짓수 너무 많거나 유사한 패턴으로 반복된다면 자료구조를 통해 if/switch 문을 대체할 수 있다.
이 때의 장점으로는 코드가 간략해져 가독성이 높아지고, 시간적 성능이 향상될 수 있다.
예제를 통해 살펴보자.

## 예제 1 - Array 이용하는 경우

예를 들어, `0`이 입력되었을 땐, `zero`가 return 되어야 하고, `1`이 입력되었을 땐, `one`이 return 되어야 하는 상황이 있다고 생각해보자. 이를 switch문으로 작성하면 아래와 같을 것이다.

```javascript
function f(num) {
    switch (num) {
        case 0:
            return 'zero';
        case 1:
            return 'one';
        case 2:
            return 'two';
        case 3:
            return 'three';
        case 4:
            return 'four';
    }
}
```

이를 Collection을 이용해 분기 처리를 하면 아래와 같이 사용할 수 있다.

```javascript
function f(num) {
    const arr = ['zero', 'one', 'two', 'three', 'four'];
    return arr[num];
}
```

코드가 훨씬 깔끔하게 작성된 것을 볼 수 있다.

## 예제 2 - Object를 이용하는 경우

예제 1번 처럼 특별한 패턴이 존재하지 않는 경우엔 JavaScript의 Object나 Map 자료구조를 사용할 수 있다. 이번엔 예제 1번과 반대로 `zero`를 입력하면 `0`을, `one`을 입력하면 `1`을 반환하도록 작성해보자.

```javascript
function f(num) {
    switch (num) {
        case 'zero':
            return 0;
        case 'one':
            return 1;
        case 'two':
            return 2;
        case 'three':
            return 3;
        case 'four':
            return 4;
    }
}
```

이를 Object를 통해 구현해보자.

```javascript
function f(num) {
    const arr = {
        zero: 0,
        one: 1,
        two: 2,
        three: 3,
        four: 4,
    };
    return arr[num];
}
```

## 예제 3 - Array와 Object를 이용하는 경우

회원가입을 하는 함수를 만든다고 생각해보자.
사용자는 id, password, name을 입력해야한다.
만약 id를 입력하지 않았을 경우엔 `아이디를 입력하세요`라는 경고 문구를 띄워야 하고, password일 땐 `비밀번호를 입력하세요`, name일 땐 `이름을 입력하세요`라고 띄워야 한다.

```javascript
function f(id, password, name) {
    if (!id) {
        alert("아이디를 입력하세요");
        return;
    } else if (!password) {
        alert("비밀번호를 입력하세요");
    } else if (!name) {
        alert("이름을 입력하세요");
        return;
    }

    // 후략
}
```

if문을 사용한다면 위와 같이 작성할 수 있다.
중복되는 코드가 많아 가독성이 떨어지는 것 같다.
이를 Array와 Object를 이용해 작성해보자.

```javascript
function f(id, password, name) {
    const arr = [
        { value: id, msg: "아이디를 입력하세요" },
        { value: password, msg: "비밀번호를 입력하세요" },
        { value: name, msg: "이름을 입력하세요" },
    ];

    for (const it of arr) {
        if (!it.value) {
            console.log(it.msg);
            return;
        }
    }

    // 후략
}
```

value와 msg를 갖는 객체를 만들어 관리하여 보다 간결한 코드가 되었다.

## 정리

분기의 개수에 따라 if문과 switch문과의 성능 차이가 발생한다.
분기가 많을 수록 if문은 오래 걸리지만 switch문은 빠른 대신 메모리를 더 많이 사용한다.
Collection을 이용해 분기 처리를 할 경우에도 메모리를 더 사용하는 대신 가독성을 얻기 때문에 상황에 맞게 if/switch/collection 방법을 사용하면 될 것 같다.