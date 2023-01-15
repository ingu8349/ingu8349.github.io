---
layout: post
title:  "useReducer에 대해 알아보자"
date:   2023-01-15 22:00:03 +0900
categories: React hook useReducer 
---

useReducer 알아보기

꽤나 많은 React Hook에 대해 알아봤는데, 통상 내가 useState 나 useEffect를 많이 사용했는데,
오늘은 useReducer에 대해서 좀 깊게 파보려고 한다. 부디 어렵지 않았으면..


## 여러개의 하위 값을 가지는 state를 다뤄야 할때 useReducer을 쓰면 효과적이다!
아예 대놓고 공식문서에 useState의 대체 함수입니다. 라고 써있구만..
다수의 하윗값을 포함하는 복잡한 정적 로직을 만드는 경우나 다음 state가 이전 state에 의존적인 경우에 보통 useState보다 useReducer를 선호합니다.

들어가기에 앞서 알아야할 것 
1. state

- 컴포넌트에서 사용할 상태

2. dispatch 함수

- 첫번째 인자인 reducer 함수를 실행시킨다.

- 컴포넌트 내에서 state의 업데이트를 일으키키 위해 사용하는 함수

3. reducer 함수

- 컴포넌트 외부에서 state를 업데이트 하는 함수

- 현재state, action 객체를 인자로 받아, 기존의 state를 대체하여 새로운 state를 반환하는 함수

4. initialState

- 초기 state

5. init

- 초기 함수 (초기 state를 조금 지연해서 생성하기 위해 사용)

## Dispatch(Action) ====> Reducer(State, Action) 이런 관점이라고 보면 될 것 같다.
```javascript
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

useState에 익숙한데 useReducder을 통해서 좀더 복잡한 state를 다룰때 사용해봐야겠다.
