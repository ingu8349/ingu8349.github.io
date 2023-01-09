---
layout: post
title:  "useContext, context Api 배워보기"
date:   2023-01-09 22:35:36 +0900
categories: useContext contextApi
---
useContext 배워보기

그간 reactHook을 꽤나 많이 써봤지만 useState, useEffect, useMemo, useCallback 외에
useContext의 존재에 대해 알게 되었다. + context Api

다른 것들을 유용하게 써왔으니, 이것에 대해도 알아보려고 한다.

## context는 앱 안에서 전역적으로 사용되는 데이터들을 여러 컴포넌트들끼리 공유할 수 있는 방법을 제공해준다.

context를 사용하면 부모에서 자식으로 하나하나 props로 데이터를 전달해 줄 필요없이 해당값에 접근할 수 있게 해준다.

- useContext는 context로 공유한 데이터들을 받아오는 react hook이다!!!
- 하지만 context를 사용하면 컴포넌트를 재사용하기 어려워 질 수 있어 꼭 필요할 때만 쓰는 것이 좋다.

쉽게 사용법은
```javascript
 const MyContext = React.createContext(defaultValue); // 으로 선언을 해서 만들고

//사용하려는 컴포넌트 바깥에다가 
<App/> //이라고 하면

<MyContext.Provider value={/* 어떤 값 */}>
    <App/>
</MyContext.Provider> // 이런식으로 감싸서 내가 원하는 자식 까지 이동을한다.
// 그리고 나서 해당 컴포넌트에서

const {defaultValue} = useContext(context이름) // 이렇게 불러와서 사용하면 된다.
```

지금까지 엄청난 props 지옥에 빠졌엇는데 이거하나로 코드를 클린하게 쓸 수 있을 것 같다!

시스템에 적용해놓은거 수정해봐이지..