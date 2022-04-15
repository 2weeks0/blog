# [JavaScript] 함수 표현식

- 자바스크립트에선 함수는 값이다. 따라서, 변수에 담을 수 있다.

```javascript
let printHello = function() {
    console.log("안녕하세요")
}

console.log(printHello) // [Function: printHello]
```

- 함수를 실행하려면 변수 이름에 괄호를 붙여주면 된다.

```javascript
function printHello() {
    console.log("안녕하세요")
}

printHello()

let printHello2 = printHello
printHello2()
```

## 콜백 함수

- 함수를 함수의 매개변수로 전달하고, 그 함수는 나중에 호출(called back)되는데, 이를 콜백 함수라고 한다.

```javascript
function ask(question, yes, no) {
    if (confirm(question)) {
        yes()
    } else {
        no()
    }
}

function showOk() {
    alert("OK")
}

function showNo() {
    alert("NO")
}

ask("동의하십니까?", showOk, showNo)
```

- 위 예에서 `showOk`, `showNo` 함수가 콜백 함수다. 사용자가 `confirm` 함수의 응답을 어떻게 했냐에 따라 `showOk` 함수, `showNo`함수가 실행된다.
- 위 예를 함수 표현식을 사용하여 다시 작성하면 아래와 같다.

```javascript
function ask(question, yes, no) {
    if (confirm(question)) {
        yes()
    } else {
        no()
    }
}

ask(
    "동의하십니까?",
    function() {
        alert("OK")
    },
    function() {
        alert("NO")
    }
)   
```

- 함수를 콜백 함수로만 사용된다면 이름을 생략하여 작성하는데, 이런 함수를 익명 함수(anonymous function)이라고 한다.

## 함수 표현식과 함수 선언문의 차이

- 함수 표현식과 함수 선언문의 큰 차이는 "함수 생성 시점"에 있다.
- 함수 표현식의 경우, 해당 변수가 생성될 때, 해당 함수가 생성되고 그 이후로부터 해당 함수를 사용할 수 있다. 
- 함수 선언문은 스크립트를 실행하기 전, 준비 단계에서 전역에 존재하는 함수 선언문을 모두 찾아 함수를 생성하기 때문에 실제 선언하는 줄과 상관 없이 함수를 사용할 수 있다.
---
- 함수 표현식 예

```javascript
printHello() // ReferenceError: Cannot access 'printHello' before initialization

let printHello = function() {
    console.log("안녕하세요")
}
```

- 함수 선언문 예

```javascript
printHello() // 안녕하세요

function printHello() {
    console.log("안녕하세요")
}
```

