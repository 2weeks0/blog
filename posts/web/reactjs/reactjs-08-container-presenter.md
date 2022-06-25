# [React.js] Container와 Presenter 디자인 패턴

## Container & Presenter 디자인 패턴이란?

- 로직을 담당하는 Container 컴포넌트와 UI를 담당하는 Presenter 컴포넌트로 나누는 패턴!
- 관심사를 분리시켜 유지보수를 용이하기 하기 위함.
- Container는 Presenter에 props로 데이터를 내려 상태를 공유

## Container

- 로직과 상태를 담당하는 컴포넌트
- Presenter 컴포넌트의 부모로 UI에 관여하지 않음 (스타일, 마크업 요소가 없다)
- Presenter에 props로 데이터와 콜백 함수들을 내려준다.

## Presenter

- UI를 담당하는 컴포넌트
- 상태나 로직을 직접 관여하지 않고, 부모인 Container에게 props를 받아 처리함.
- 혹, 상태가 필요하다면 UI와 관련된 단순한 상태여야 함.

## Container 예제

```javascript
import { useDispatch, useSelector } from "react-redux";

import { selectSort, setSort } from "../../store/slices/sortSlice";

import ProblemListHeader from "./ProblemListHeader";

export default function ProblemListHeaderContainer() {
  const sort = useSelector(selectSort);
  const dispatch = useDispatch();
  const handleClick = (key) => {
    dispatch(setSort(key));
  };

  return <ProblemListHeader sort={sort} onClick={handleClick} />;
}
```

데이터인 `sort`와 클릭 이벤트 콜백 함수인 `handleClick`를 Presenter 컴포넌트에게 넘겨주는 역할을 한다.


## Presenter 예제

```javascript
import PropsTypes from "prop-types";

const propsType = {
  sort: PropsTypes.object,
  onClick: PropsTypes.func,
};

const defaultProps = {
  onClick: () => console.error("ProblemListHeader에 onClick 넘겨주세요"),
};

export default function ProblemListHeader(props) {
  const headerList = [
    {
      col: "1",
      key: "id",
      name: "번호",
    },
    {
      col: "1",
      key: "level",
      name: "티어",
    },
    {
      col: "6",
      key: "title",
      name: "문제 이름",
    },
    {
      col: "2",
      key: "solved",
      name: "정답자 수",
    },
    {
      col: "2",
      key: "average_try",
      name: "평균 시도 횟수",
    },
  ];

  const arrowUp = String.fromCodePoint(0x2b06);
  const arrowDown = String.fromCodePoint(0x2b07);

  return (
    <thead>
      <tr>
        {headerList.map((it) => (
          <th className={`col-${it.col}`} key={it.key}>
            <button className="btn p-0" onClick={() => props.onClick(it.key)}>
              <strong>{it.name}</strong>
              {props.sort.key === it.key
                ? props.sort.direction === "asc"
                  ? arrowUp
                  : arrowDown
                : null}
            </button>
          </th>
        ))}
      </tr>
    </thead>
  );
}

ProblemListHeader.propsType = propsType;
ProblemListHeader.defaultProps = defaultProps;
```

