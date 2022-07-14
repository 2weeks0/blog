# [React.js] `ref` vs `reactive`

Vue 3에서 반응형 데이터를 사용할 때, `ref` 또는 `reactive`를 사용한다. `ref`와 `reactive`의 차이를 알아보자.

## 차이점

1. `ref`는 원시 타입의 인자를 받을 수 있지만, `reactive`는 object 객체만 받을 수 있다.

    ```javascript
    const useRef = ref(0); // VALID

    const useReactive = reactive(0); // INVALID
    ```

    `ref`에서도 object 객체를 받을 수 있다.

    ```javascript
    const useRef = ref({ count: 0 }); // VALID

    const useReactive = reactive({ count: 0 }); // VALID
    ```

2. `setup` 내에서 `ref`로 생성한 state의 값에 접근하려할 경우, `.value`를 붙여줘야 한다. 하지만 `reactive`로 생성했을 경우엔 바로 접근할 수 있다.

    ```javascript
    const useRef = ref({ count: 0 });
    console.log(useRef.value.count); // 0

    const useReactive = reactive({ count: 0 });
    console.log(useReactive.count); // 0
    ```

    `template`에서 사용할 땐, `.value`를 안붙여도 된다.

    ```javascript
    <template>
    useRef.count: {{ useRef.count }}
    useReactive.count: {{ useReactive.count }}
    </template>

    <script setup>
    import {ref, reactive} from "vue"

    const useRef = ref({count:0});
    const useReactive = reactive({count:0});
    </script>
    ```

3. `ref`는 인스턴스 자체를 변경할 수 있지만, `reactive`는 불가능하다.

    ```javascript
    const useRef = ref({ count: 0 });
    useRef.value = {count: 1}; // VALID

    const useReactive = reactive({ count: 0 });
    useReactive.value = {count: 1}; // INVALID
    ```

## 언제 `reactive`를 사용하나?

`ref`의 사용처는 분명하다. 원시 타입을 다룰 때 사용한다. `reactive`로는 불가능하기 때문인다. 하지만 `reactive`는 `ref`가 `reactive`의 기능을 포함하니, `reactive`의 사용처에 대해 의문을 가질 수 있다.

`reactive`의 장점은 `.value`를 사용하지 않아도 된다는 점, 차이점 3번과 같이 인스턴스 자체를 변경할 수 없다는 점이 있다. 이는 Options API의 `data`와 유사하다. state를 하나의 object를 묶어 각각을 관리할 때, `reactive`가 용이하고, 안전하다.