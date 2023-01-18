---
layout: post
title:  "state와 lifecycle"
date:   2023-01-18 22:00:03 +0900
categories: react state lifecycle
---

react 공식 문서를 보며 state lifecycle를 이해하다.

공식문서를 보면 참 깔끔하게 나와있네 생각이 들면서도 말들이 참 어렵다는 생각이 든다.

그래도 저번에 실제 업무에서 lifeCycle의 중요함을 듣고나서 한 번 정리를 해두면 좋겠다는 생각이 들어 한 개의 주제로 삼기로 했다.

## state 리엑트에서 component의 변경 가능한 데이터를 나타낸다. 리엑트 컴포넌트의 변경 가능 한 데이터!

알다시피 state가 변경될 경우 컴포넌트가 재렌더링 되기 때문에 렌더링 이나 데이터 흐름에 필요한 데이터만 state로 지정해줘야한다.

## state는 javascript 객체이다.

```javascript
class LikeButton extends React.component {
    constuctor(props) {
        super(props);
        this.state = {
            liked: false
        }
    }
}

//잘못된 수정법
this.state={
    name: "inje"
}
// 옳은 수정법
this.setState({name: "inje"})
```

## state는 직접 수정하면 안된다. (할 수는 있다. 하지만 불가능하다고 생각하는 것이 좋다.)
그래서 꼭 setState를 이용해 변경할 필요가 있다.

----------------------------------------------

두번째 lifecycle 생명주기

## 쉽게 react component가 생성되고, 사라지는 주기

mounting ----- undating ------ unmounting 의 순으로 흘러간다.

updating이 될 때는
1. New props : props가 변경되거나
2. setState() :setState함수 호출에 의해 state가 변경되거나
3. forceUpdate() : forceUpdate()라는 함수에 의해 강제 업데이트 되거나 

생명주기의 흐름에 따라 생성되는 class 컴포넌트의 함수
## 생명주기 함수
componentDidMount ----- componentDidUpdate ----- componentWillUnMount

componentWillUnMount 언제될까? 
= 상위 component에서 현재 component를 더 이상 화면에 표시하지 않을 때

![img.png](img.png) // 출처 velog ( https://velog.io/@dea8307/React-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4Life-Cycle-%EC%9D%B4%ED%95%B4 )


##이런 형태로 굴러간다고 머리 속에 생명주기를 넣어놔야 겠다. 끝 